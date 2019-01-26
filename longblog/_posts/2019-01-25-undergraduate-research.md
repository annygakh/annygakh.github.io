---
layout: post
category: longblog
title: My experience with undergraduate research
published: true
---

- [My experience](#my-experience)
  * [Approaching a professor](#approaching-a-professor)
  * [Choosing a project](#choosing-a-project)
  * [What I worked on](#what-i-worked-on)
  * [Getting Help](#getting-help)
  * [Weekly activities](#weekly-activities)
    + [NSS Seminar](#nss-seminar)
    + [Progress Reports](#progress-reports)
  * [Keeping track of tasks](#keeping-track-of-tasks)
- [Reflection](#reflection)
  * [What I learned](#what-i-learned)
  * [Challenges](#challenges)
- [Advice to others](#advice-to-others)
- [Summary](#summary)

## My experience
### Approaching a professor
In the spring semester of 2018 I took [CPSC 416](https://www.cs.ubc.ca/~bestchai/teaching/cs416_2018w1/index.html) Distributed Systems with Ivan Beschastnikh. I really enjoyed the course and wanted to learn more about distributed systems, but I wasn’t sure what my next steps could be. So I scheduled a meeting with Ivan and he gave me lots of ideas - I could take a graduate distributed systems course next year (in spring of 2019), I could experiment with building distributed applications on my own, and/or I could take a directed studies course where he would be my supervisor. I decided that I would like to do a directed studies course and so that is what I am writing about today. So what is a directed studies course? Well, it is one of the ways an undergraduate student at UBC can get a glimpse of what it’s like to do research in computer science. You can learn more [here](https://www.cs.ubc.ca/students/undergrad/courses/specialty) about this, but the basic idea is that a student can get 3 credits, as they would for another CPSC course, and they work on either an existing research project (perhaps with other students - graduate or undergraduate) or a new research project.

### Choosing a project
When it came time to choose what I would work on, I did not have a specific area I wanted to focus on, as my interests are pretty broad - instead, I just knew of a few areas I wasn’t interested in (e.g., formal verification). Ivan had sent me papers (for projects) that were submitted to either past conferences or were about to be submitted to a conference so I could get an idea of which students I should approach to find out more about projects I was interested in. I was also told that when choosing a project I should ensure that my work style was compatible with the students who are responsible for the project and that I am comfortable working with them. In addition I was advised to not hold back in asking hard questions - the kinds of questions one might ask when wanting to find out more about their team/manager before joining a new company.

I met with several MSc and PhD students in the lab and eventually settled on a project. Initially, I was going to work on a project related to ["Inter-process communication in disaggregated datacenters"](https://www.cs.ubc.ca/~bestchai/theses/amanda-carbonari-msc-thesis-2018.pdf) with [Fabian](https://www.cs.ubc.ca/~fruffy/)  and it was going to be a new project picking up from Masters thesis of a former MSc student. Fabian has sent me lots of related work to read and ponder on and he also gave me access to two lab machines which I could use for my work. I also had to learn a bit about how distributed TensorFlow works and I even wrote about it [here](https://annygakh.github.io/longblog/2018/09/13/TensorFlow.html).
However, during one of the meetings, Ivan has brought up a [paper](https://www.usenix.org/legacy/event/usenix08/tech/full_papers/menon/menon_html/paper.html) he has read  pointing out ACK offloading into network stack as one of the contributions of the paper. Then, an idea for a new project was born. In a situation where there are two hosts and one switch, with one host sending data via switch to another host, ACK offloading could potentially increase throughput if done at the NIC (see ["What I worked on"](#what-i-worked-on) below for more details). When I expressed interest in working on this, it was decided this work would be more useful if done as part of another project, [JumpGate](https://ece.ubc.ca/~craigm/papers/jumpgate2018osdi.pdf), on which another PhD student, [Craig](https://ece.ubc.ca/~craigm/) was working on with Fabian.

### What I worked on
What does it mean for ACK offloading to take place at the NIC? The idea is that if host 1 is sending data via TCP/SCTP to host 2, the switch can send ACKs to host 1 on behalf of host 2. If ACK generation no longer depends on the CPU of the host, it leads to decreased latency and reduced variance which would be beneficial for JumpGate project, since it is about in-network data processing.

Luckily, I didn’t have to go through tedious network setup with multiple machines when working on ACK forwarding. To avoid having to recreate the actual network, Craig and Fabian set up a virtual network using [Mininet](http://mininet.org/) which could be run on just one machine. The initial code at the switch in the network was very simple - if it received a packet from host 2, it would forward it to host 1 and vice versa.

The first prototype of ACK offloading was done in Python using [Scapy](https://scapy.net/) in order to keep the implementation simple and understand what needs to be done for ACK offloading to work properly. To be able to construct an ACK in response to a TCP message, I, first, had to understand the TCP state machine by reading the RFC. Additionally, I inspected the contents of the TCP packets from packet captures of simple data exchange between two hosts to visualize how values of different fields in the packet change.

In order to gauge how slow ACK forwarding in Python + Scapy was, I timed how long it took to send a packet and get a response when the ACK forwarding was enabled vs when it was disabled, both in Python + Scapy, by parsing timestamps from packet capture files. The ACK forwarding was very slow, even when the code has undergone changes in order to make two code paths as similar as possible. This is not desirable as the entire purpose of ACK offloading is to speed up the TCP data transfer and to eliminate ACKs being the bottleneck of the TCP send rate. My next step was to implement ACK acknowledgement using [eBPF](https://lwn.net/Articles/740157/) and [XDP](https://www.iovisor.org/technology/xdp).

eBPF and XDP allow users to insert custom code at the network stack entry point of when a packet is received or sent in order to speed up packet processing. Packets received can be sent and received on a special socket, called AF XDP, in order to bypass layers of the protocol stack.
 The idea is to set up an XDP program that will send packets from the sender host to AF XDP socket #1 and to receiver host. In a C program, in response to packets from AF XDP socket #1 an ACK will be created and sent via AF XDP socket #2. The same XDP program upon receiving an ACK via AF XDP socket #2 will forward the packet to host 1. Unlike eBPF and XDP, AF XDP sockets don't have many tutorials or examples illustrating their use, besides [code examples](https://elixir.bootlin.com/linux/v4.20.3/source/samples/bpf/xdpsock_user.c) that live in Linux kernel repository , so Fabian has helped me go through some of the code examples and understand them. Another source of help I discovered is [xdp-newbies](http://vger.kernel.org/vger-lists.html#xdp-newbies) - a mailing list that David Miller has created.

Since XDP + TCP + namespaces [does not work](https://www.spinics.net/lists/xdp-newbies/msg00448.html) in Linux, we needed to use a different protocol, namely SCTP. I had to read the RFC about how it works and finished an implementation in Python + Scapy. The next steps are to implement ACK forwarding for SCTP using eBPF and XDP, which is currently still in progress!

Since Craig was going to submit a paper for JumpGate to [HotOS](https://www.sigops.org/2018/hotos2019/) I had to pause work on ACK forwarding in December and instead work on running various benchmarks that would be included in the paper. My task was to measure the performance of various queries in Spark, as more and more preprocessing was done before the query was run. The results from running benchmarks helped motivate the need for in-network data processing. While working on my task, I have learned some specifics about Spark internals and have managed to write some Scala. Towards the submission deadline I ended up working closely with Craig when experimenting with different ways of running the benchmarks and I found it to be very rewarding and insightful. Our experiments have shown that in-network processing could improve our Spark query by up to 16x! Another exciting thing is that I am now a coauthor of a paper :) I will update this post with a link when the paper will become available.

### Getting Help
Throughout the semester I always felt that I had help available, if I ever got stuck. At the beginning of the semester, Ivan, Craig, Fabian and I had weekly meetings, where, among other things, I could discuss my progress on the project and we would talk about other ideas that can be explored. When we didn't have weekly meetings, I would meet with Craig or Fabian and brainstorm ideas with them and ask them for help with any issues I was having.


### Weekly activities
After I had chosen a project to work on and submitted my application to take a directed studies course, I became a member of the [NSS lab](https://www.cs.ubc.ca/labs/nss/html/index.html). Being a part of the NSS lab is not just about working on a project and meeting with your supervisor and other project members. It also consists of a weekly seminar, sending out progress reports, and more. I will describe the first two in detail.
#### NSS Seminar
Once a week a member of the NSS lab presents a paper from one of the conferences such as [OSDI](https://www.usenix.org/conferences/byname/179), [NSDI](https://www.usenix.org/conferences/byname/178), [Eurosys](https://dl.acm.org/event.cfm?id=RE101), [Sigcomm](http://www.sigcomm.org/), etc. The other members are supposed to read the paper before the seminar, and after the presentation, people evaluate the paper out loud and discuss its advantages and disadvantages. This was one of my favourite parts this semester! Even though frequently I did not understand a lot of details from the paper, I found it very valuable to hear the discussions between others because it showed me what others pay attention to when reading papers and how they evaluate papers. One time, everyone was discussing the [NetHide](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-meier.pdf) paper and someone asked if the same technique could be applied to code obfuscation (think JS code obfuscation) and I think this question was very fascinating because I wouldn’t have thought to compare those two techniques.

The way I prepared for the seminars was to read the paper the day before and try to understand the general idea behind it. During the presentation I would write down any mentioned terms/techniques I haven’t heard of before. Since that might be an overwhelming amount of things, I wouldn’t look them up right away. During the next seminar, I would do the same thing. After a few seminars I would note any terms/techniques that came up over and over again because it signified to me that it’s something I should definitely read up on and understand in greater detail.

Here are some example papers we looked at, one example per conference:
- [OSDI'18 - The FuzzyLog: A Partially Ordered Shared Log](https://www.usenix.org/system/files/osdi18-lockerman.pdf)
- [NSDI'18 - ResQ: Enabling SLOs in Network Function Virtualization](https://www.usenix.org/system/files/conference/nsdi18/nsdi18-tootoonchian.pdf)
- [Eurosys'18 - Delta Pointers: Buffer Overflow Checks Without the Checks](https://www.cs.vu.nl/~herbertb/download/papers/delta-pointers_eurosys18.pdf)
- [Sigcomm'18 - Automated synthesis of adversarial workloads for network functions](https://dl.acm.org/citation.cfm?id=3230573)


#### Progress Reports
Most of the students who have weekly meetings with Ivan are expected to send out a progress report the day before their project meeting. The point of progress reports is to communicate the work a student has done during the week, their troubles (if any) and the work they are planning to do next week. A progress report is not sent solely to the other members of the project and the supervisor, but to a dedicated mailing list. Most of the students from the NSS lab are on that mailing list. This gives everyone a chance to know about what other people are working on and sometimes even the opportunity to help someone else. Note that sending out progress reports is just one aspect of working with Ivan, and other professors will have different processes in place for students to communicate their work.

### Keeping track of tasks
Keeping track of tasks when working on a research project can be a bit overwhelming, especially when there are lots of new ideas being formed during meetings. I like to keep a text document where I write down all of the tasks I need to do and what I work on each day. This helps me with writing my progress reports too, so I don’t have to struggle with remembering what I did during the week.

Here is an example:

    [ ] Run measurements
      [ ] I have run into problem, ask Y about it
    [X] Implement Z
        [ ] Maybe we can add A, B, C to it
        [ ] Since we did Z, maybe we could do E, F, G then?


## Reflection
### What I learned
My project was related to networking, so I learned a great deal about TCP and SCTP protocols, network and transport layers in Linux, BPF virtual machine and XDP programs, mininet simulations, and more. But the most important thing I learned was the scientific approach to computer science. The advice I have always received from the people who were helping me with my work was - do the simplest thing to make it work in the best case scenario and you can improve it afterwards. I believe this approach is applicable not only in academic research, but also in the industry as it reinforces an idea that I think is very important - start simple! In addition to starting simple, I discovered that when trying to solve a certain problem it is important to view your work through the eyes of others and ask questions such as “why didn’t you try this simpler thing? If it didn’t solve the problem you are trying to solve or if it wasn’t efficient enough, what were its disadvantages? What’s the next simplest thing you could try to make it work?”. It’s important to consider all of these questions because it shows that you follow a scientific approach in your design.
### Challenges
Sometimes I found it challenging to conceive new ideas to explore as part of my research project, and I think it’s because most of my experience consists of building things following a specification (e.g., a class assignment or a feature at work) or with a concrete end goal in mind (e.g., I would like to build an app that allows me to stream music into several bluetooth headphones or I need to build a tool to re-encrypt certain sql tables at work). I think the solution to this creative slowdown is to simply read more papers from recent conferences and to not shy away from reading papers on topics that are not of immediate interest to me, in order to build up a collection of research questions that other people ask and to understand the methodology used to answer those research questions. Despite finding it challenging, I really enjoyed having the freedom to explore various directions and experimenting with various technologies.

## Advice to others
In this section I will try to answer some questions that I think someone wanting to embark on the same journey as I did would find useful. These questions are a result of me trying to find out what other undergraduate students would like to know should they choose to take a directed studies course or approach a professor to do research with them. I will also try to give some advice based on my experience.

- Q: How do you approach a professor to ask them if you can work on something in their lab or under their supervision?
    - I already described how I approached my supervisor, but I must mention that I wish I had more courage to approach professors in my previous courses. I hadn’t done it earlier because I had imposter syndrome, but something that you should keep in mind is that - if you are interested in working on something and are willing to commit, you should go ahead and ask the professor about it! You might also want to approach graduate TAs, who are MSc or PhD students and would appreciate help.
- Q: How much flexibility does a student have in choosing a project to work on?
    - Sometimes students might not have the leisure of choosing which project to work on - this might be because a student hasn’t taken certain upper level classes and lacks certain experience that a project requires or it might be that a project has too many people working on it. If none of the projects in the lab are something that you want to work on, you can try to propose a new idea that can be an extension of an existing project in the lab. There are often multiple active faculty members in the same lab, whom you can approach about projects.
- Q: I would love to do research full time for a semester and maybe have it count as a COOP semester. Is that possible?
    - Yes! You might want to checkout programs such as [USRA](https://www.cs.ubc.ca/students/undergrad/research-competitions/getting-involved-research). You can also get awards for undergraduate research via programs such as [SURE](http://science.ubc.ca/students/resources/research) and [WLIUR](https://students.ubc.ca/career/campus-experiences/undergraduate-research/work-learn-international-undergraduate-research-awards).

And here is some advice - if you have enough time and you belong to a lab where you frequently interact with other students, try to find out how you can help others with your skills. Perhaps, someone would like to experiment with an idea, tangential to their project and requires the knowledge of some niche technology that you happen to know very well and one they don’t have the time to learn and explore. This is a great opportunity to get involved and work on another project, even temporarily. However, it might not be always the case that someone will exclaim “I wish I could explore idea X using <some niche technology> but I just don’t have the time for it”, so pay attention to the obstacles others are having with their projects and try to think of ways to help out using what you know.

## Summary
Some lessons learned in no particular order:
- Keeping track of your work in a text document keeps you sane and on track
- Start simple - implement the simplest thing in the best case scenario and gradually iterate on your implementation
- Be able to explain the reasoning behind the implementation design you chose and give the cons and pros of other approaches
- Take advantage of reading groups and try to attend as many meetings as you can
- If you have time, figure out how to help others in the lab with their projects
- Reading papers and learning how to evaluate them is a very important skill

In conclusion, doing undergraduate research was a blast! I found NSS seminars and discussions with others valuable in helping me think critically about ideas proposed by others. I gained a lot of technical knowledge, and learned how to approach implementation of system design in an efficient and well thought-out manner. Even though I faced challenges when thinking of new directions for my research, I have outlined ways to help me become a better researcher in the future. Without making any attempt to sound less vague, to anyone who wants to solve problems in computer science, I would recommend taking a directed studies course as early as they can. And as for me, my next step is to audit an [Graduate Operating Systems Course](https://www.seltzer.com/margo/teaching/CS508.19/index.html) to immerse myself in discussing systems research in a grad course setting.






