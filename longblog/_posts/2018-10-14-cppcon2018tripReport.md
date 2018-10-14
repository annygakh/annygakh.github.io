---
layout: post
category: longblog
title: CppCon 2018 Trip report
published: true
---

CppCon2018 ended two weeks ago and I have been unable to write about it until now. A week away from school required me to catch up on a lot of material and assignments once I got back and that's why it took me so long to write this. While I am still not free of school stress, at least I have time to describe how I ended up at CppCon 2018, how it was and what I learned. Spoiler alert: it was life-changing! :)

# Outline
This post is very long, so here is an outline of Things. If you don't have much time, I suggest you read the [summary](#summary). I also have handwritten (sketch?)notes [here](/assets/pdfs/annygakhCppcon2018notes.pdf). And here is a preview of some of my notes
![Image](/assets/images/cppcon2018/jefftrullgdbpython.jpg)
![Image](/assets/images/cppcon2018/whatdowemeannothing.jpg)
![Image](/assets/images/cppcon2018/simonbranddebuggers.jpg)
![Image](/assets/images/cppcon2018/herbSutterMeta.jpg)


- [How I heard about CppCon](#how-i-heard-about-cppcon)
- [Registering for CppCon 2018](#registering-for-cppcon-2018)
- [About Women In Tech Fund and #include_cpp](#about-women-in-tech-fund-and-include_cpp)
- [The weekend before CppCon](#the-weekend-before-cppcon)
- [Day 1 - Monday, Sept 24, 2018](#day-1---monday-sept-24-2018)
  - [Bjarne Stroustrup - Concepts: The Future of Generic Programming](#bjarne-stroustrup---concepts-the-future-of-generic-programming)
  - [Matthew Butler - Secure Coding Best Practices: Your First Line Is The Last Line Of Defense (1/2)](#matthew-butler---secure-coding-best-practices-your-first-line-is-the-last-line-of-defense-12)
  - [Lunch](#lunch)
  - [Simon Brand - How C++ Debuggers Work](#simon-brand---how-c-debuggers-work)
  - [Student Dinner](#student-dinner)
  - [Grill the Committee](#grill-the-committee)
- [Day 2 - Tuesday, Sept 25, 2018](#day-2---tuesday-sept-25-2018)
  - [Kate Gregory - What Do We Mean When We Say Nothing At All?](#kate-gregory---what-do-we-mean-when-we-say-nothing-at-all)
  - [Greg Law - More gdb and other Linux debugging wizardry](#greg-law---more-gdb-and-other-linux-debugging-wizardry)
  - [Richard Powell - Named Arguments](#richard-powell---named-arguments)
  - [#include_cpp dinner](#include-cpp-dinner)
- [Day 3 - Wednesday, Sept 26, 2018](#day-3---wednesday-sept-26-2018)
  - [Patricia Aas - Software Vulnerabilities](#patricia-aas---software-vulnerabilities)
  - [Kate Gregory - Simplicity](#kate-gregory---simplicity)
  - [C++ Community Building BoF](#c-community-building-bof)
  - [Serge Guelton - C++ in Elvenland](#serge-guelton---c-in-elvenland)
  - [Lighting Talks](#lighting-talks)
- [Day 4 - Thursday, Sept 27, 2018](#day-4---thursday-sept-27-2018)
  - [Herb Sutter - Thoughts on a More Powerful And Simpler C++](#herb-sutter---thoughts-on-a-more-powerful-and-simpler-c)
  - [Jeff Trull - Liberating the Debugging Experience with the GDB Python API](#jeff-trull---liberating-the-debugging-experience-with-the-gdb-python-api)
  - [My Lighting Talk](#my-lighting-talk)
- [Day 5 - Friday, Sept 28, 2018](#day-5---friday-sept-28-2018)
- [Summary](#summary)
  - [Reflection](#reflection-1)
  - [Other Random Good Things That Happened To Me In No Particular Order](#other-random-good-things-that-happened-to-me-in-no-particular-order)
  - [Thank You](#thank-you)


# How I heard about CppCon
C++ is one of my favourite programming languages and I like anything to do with C++. Around two years ago I discovered CppCon conference videos online, and have watched quite a few talks since then. Then I thought it must be so cool to attend this conference, watch speakers present different things one can do in C++ and meet people who are interested in the same things as you.

# Registering for CppCon 2018
This August, I was looking to see which conferences were happening nearby me and to my surprise I have realized that CppCon has always been in Bellevue (I am in Vancouver, Canada) and it was going to be held quite soon! Then I discovered that [Women In Tech Fund](https://womenintechfund.org) was accepting applications from women who are in need of financial assistance to be able to attend the conference. I wrote about how I would benefit from attending such conference and what I hope to get out of it and submitted my application.

The next day I have received a reply saying that my application has been accepted. Wow! It was a really happy day for me. After some time I was contacted by the organizers of the CppCon and they helped me register for CppCon and ensured that I had a place to stay for the duration of the conference.

# About Women In Tech Fund and #include_cpp
I would like to share some information about [@WomenInTechFund](https://womenintechfund.org) and [@include_cpp](https://www.includecpp.org/) because I think those are awesome organizations/communities that everyone should know about!

First, a little bit about Independent Fund for Women in Tech (@WomenInTechFund)
> The Independent Women in Tech Fund aims to help women attend security conferences by providing assistance with entry ticket and possible travel support. [...]
> For most women, the opportunity to attend  conferences, talk to peers, see other women in the field, ask for advices and feel that they are supported makes a difference in their careers. Such support may help decide their future. We want to help with that.

And a little bit about #include_cpp
> #include<C++> is a global, inclusive, and diverse community for developers interested in C++. Here, you can find a welcoming space to learn and discuss C++. We also provide resources to create safer, more inclusive, community gatherings.
>
> We believe that a community is only as good as how it treats its most vulnerable members. Therefore, we strive to create a welcoming, safe, and accessible environment. You can find our code of conduct [here](https://www.includecpp.org/code-of-conduct).

So what's going on? :) What happened and how did the two organizations work together to help women (cis and trans) to attend CppCon? To summarize the story from the [gofundme campaign](https://www.gofundme.com/sponsoring-women-CppCon-a) - #include_cpp has been in contact with the Women in Tech Fund and CppCon organizers, and were raising money for women to attend this conference. And Women In Tech Fund was administering the tickets.

43 people have donated to this cause! That is super awesome!

# The weekend before CppCon
## Reaching out to people on Twitter
I wanted to do a shout out to Women In Tech Fund, #include_cpp and the 43 donors, so I thanked them on Twitter (since all the cool people are hanging out on Twitter) and then my tweet got a lot of retweets! People were very nice and told me
- they were glad I get a chance to attend CppCon
- they wanted to meet me and I should find them when I have a chance
- they would gladly introduce me to other people

I also reached out myself to a few other people who were tweeting under #IGotYourBack, and I tweeted to them thanking them and saying that I hope I get to meet them at the conference.

## Deciding which talks to attend
Now that I was going to CppCon for sure, I needed to decide which talks I should attend. It was. Really. Overwhelming. I wrote about it [here](http://annygakh.github.io/longblog/2018/09/22/prereadingCppCon2018talks.html). To summarize - I went through the description of each talk carefully, and wrote down what I know already in relation to the topic and what I hope to learn about it. I also tweeted about it and people liked it as well!

# Day 0 - Sunday, Sept 23, 2018
## Cpp Tee Shirt Dinner
I call it day 0 because the official talks did not begin until the next day. My plan for the day was to bus to Bellevue from Vancouver, to attend a Cpp Tee Shirt Dinner and to attend a reception. From what I understand, this dinner is sort of like a tradition, and you are supposed to wear a Cpp tshirt and go to one of the pre-selected restaraunts, alone or with a group. This gives people a chance to mingle and meet new people. Since I didn't know anybody, I was really excited to attend the dinner. Also, on twitter, CppCon folks were sharing the names of the restaunts they were planning to head to, which was helpful. In the morning @pati_gallardo reached out to me, which was very very nice of her, and I decided I would go to the same restaraunt as her so I could meet her in person! I went there and met her and quite a few other people (spoiler alert # 1: they were super awesome people) and I had such a great time. I got to know some folks, where they work, what they work on and etc. We sat there for two hours or so and more and more people were joining, which was awesome!

## Reception
After the dinner there was a reception back in the convention center and we went there. It was Patricia's first time at the CppCon, but she already knew quite a few people and she made sure to introduce me to everyone she knew and anyone else that I wanted to meet. That. Was. Super. Fun! Everyone was so **nice** and interesting to talk to! Quite a few of them were folks I briefly interacted on Twitter. I had good conversations with people, learned new things (e.g. monads in C++) and met some people whose work I have seen before - e.g. Rob from @cppcast!!! what!! I used to listen to that podcast all the time while commuting to university. I also chatted with @hankadusikova and @michaelcaisse and they convinced me to do a lighting talk (spoiler alert #2: I did it)!

## Reflection
I came back to my hotel and couldn't stop smiling because I was really happy. I couldn't believe how welcoming and nice everyone was. I got to participate in so many interesting conversations and no one acted condescending if I asked something that everyone else might have already known - quite the opposite - they were very eager to explain.

# Day 1 - Monday, Sept 24, 2018
Finally, I will talk about the talks I have seen. But first, a little disclaimer - I'm going to talk about what I took away from the talks. Sometimes the talks went over my head and I was only able to write down keywords and ideas I need to read up on. I think that's okay! I also took lots of notes (with doodles of course) and I posted them on twitter and will be attaching them here as well. A lot of info that is contained in my notes will be repeated here because I'm looking over my notes and typing them up here into cohesive paragraphs.

## Bjarne Stroustrup - Concepts: The Future of Generic Programming
This talk was not really oriented at technical language details. Bjarne said that individual features in isolation from the language are not the intent here. The goal of the talk was to improve generic programming so it becomes as simple as non-generic code, but to achieve that, we need to improve other features.

One might try to find similarities between Types and Concepts. Roughly put, Types specify the set of operations for an object. With Concepts, however, you specify how one can use an object, and it is not just for functions or classes.

Some advantages of concepts include:
- readability
- maintainability

Great! Let's look at some properties of Concepts:
#### (Some) Properties of Concepts
**Conditional properties**

This allows you to express the following idea in the code "make it so -> operator can only be used if other is a class". Hold on, can't we use `std::enable_if` for this? Well no, they don't really scale and lots of workarounds are needed.

**Reliability**

Sometimes `auto` is misused, like in the following example
```cpp
auto x = foo(1); // x is InputChannel
```
The above code is not really maintainable and the comment contains a requirement that can't be enforced by the compiler.

Fear not, because with Concepts you can do this:
```cpp
InputChannel x = foo(1);
```
**+** This is readable and can be enforced by the compiler.

#### Concept of Concepts
Concepts aren't really a new thing! Think of **compile time predicates** - they are quite fundamental and we have had them for a while. Examples include
- developer's head
- documentation
- code comments

But now, we get to represent those ideas in code! To summarize, I will list (some) of the pros again:

**+** Concepts are flexible and allow you to keep extending and working on them (because you probably won't get it right  the first time)

**+** Once you use concepts you won't go back because you begin thinking in terms of them

**+** You express ideas more clearly so **even a compiler can understand**

This change is not a detail, but a change in how we think, so it is a major change, and that's is why it might take a while to get adopted.
#### Thoughts
I thought this talk was informative and now I understand the appeal and importance of Concepts. I also found this talk interesting because Bjarne stressed how this change is quite fundamental and it will change how we will think about it.

## Lunch
I thought it was important to talk about how my lunch was, given that I was very worried about being alone at this conference. I joined the #include_cpp discord on Sunday and I thought I would ask on the #CppCon channel if anyone wanted to get lunch together. Folks from #include_cpp had a booth for first two days of the conference, and so it happened that we would gather there at lunch time and head to some food place. It was very nice and I enjoyed speaking to people in informal settings about what they work on and what they do, and to get to know more people from the community.

I also thought it was very cool that at first it would be a small group of us waiting to go out for lunch and then 10 minutes later when we are actually heading out of the convention center, 5 more people have joined.

## Matthew Butler - Secure Coding Best Practices: Your First Line Is The Last Line Of Defense (1/2)
So, unfortunately, I was only able to go to the first part of the talk, because during the second part of the talk I really wanted to attend Simon Brand's talk on 'How C++ Debuggers work', but, I think I learned quite a few new things even from only one part of the talk. So here are my notes!
#### Intro
So some companies might think that they don't really need to care much about security. Here are 3 Reasons Why A Company Thinks They Are Safe From Attackers
- **presence of firewalls** - unfortunately, it alone did not save other companies.
- **code review and tests** - code reviews are not focused on finding exploits
- **we are too {small,big,etc} to be a target** - if you are a big company, you have lots to lose, and if you are a small company, your security is (most likely) too weak. As a result, you are always a target.

#### Terms
It might be helpful to define what a **critical system** is. A critical system is any system, regardless of its priority, that any other systems can interact with. An example is a wireless printer. Matthew told a story from his life of a time when a printer in the lab(?) of someone he knew was used to infiltrate the system.

Another term that needs to be defined is **attack vector**. Attack vectors are anything that one from outside can get into, e.g. command line interfaces.

#### Techniques
So, how do you make your programs safer? You need to remember to
1. Validate incoming arguments
2. Study the standard
3. And remember **warnings are errors**. Listen to them!

While these are not comprehensive, it might also help to know some of the things that Matthew Butler will look for when penetrating a system:
- `copy`/`moves` of memory
- not validating input data or verifying the sender
- use of open source libraries
  - their weaknesses are your weaknesses
- unguarded internal interfaces
  - don't assume inside systems to be safe!
- complexity in code design

#### Thoughts
It was very interesting! There was also an explanation (or a live demo) of buffer overflows, and I always find those to be fun. I wrote down some things I should look up again, because I forgot the details of how they work
- ASLR - randomizing address space
- Stack canaries - putting known bit patterns that needs to be checked before returning from a function. The code can abort if the canary is incorrect. And all of this is enforced by the compiler!
- Return oriented programming

## Simon Brand - How C++ Debuggers Work

#### ELF  and DWARF
**ELF** is a binary format for executable and it has headers and other useful things. There is also another format **DWARF** and it is a *debug info format*. It describes stuff about your program, e.g. what functions you have and what types they return, what types you have, etc. Debuggers usually consume DWARF, but sometimes ELF is enough for your debugger but usually for complicated things your debugger needs more info.

#### Breakpoints
So what are some things that come to your mind when you think of debuggers? I think of breakpoints. Turns out there are hardware breakpoints and software breakpoints.

**Hardware breakpoints** have special registers, but the number of them is limited. They can break on `read`/`write`/`execute` of a certain address. In `x86` there are only 4 registers and I think you have to write the breakpoint address into those registers.

**Software breakpoints** are implemented in software. The running code is modified so that a breakpoint occurs. You can have an unlimited number of breakpoints. A limitation is that they can only break on `execute`. In `x86` you have to replace the current instruction with `int3`.

#### Other random bits and bobs
These are some definitions and notes I took down regarding some concepts. They are a bit messy and have no story connecting them because some of this stuff went over my head :)
- **mangling** is cool! each function gets mangled differently and the process differs from compiler to compiler.
- `process_vm_ready` reads more than one page at a time??
- **DW-tag subprogram** - each function in DWARF has entries for its beginning and end. This allows you to compare current PC to ranges of each function and discover the exact name of the current function that is being processed.
- DWARF gives you info about inlined functions.
- things related to **shared libraries **
  - **r_debug**
  - **link_map** - tells you of all shared libraries
  - **r_brk__** - gets called when a library is being called

#### Thoughts
This was a super interesting talk( and topic) and my plan for when I have some more time is to read about all of this in greater detail. During the talk I had some questions that I'm sure I can answer once I start researching some more (or rewatch the talk)
1. How is DWARF generated?
2. What exactly happens when an instruction is replaced with `int3`?
3. How do line breakpoints work? What's the process of generating those?
4. How does `step out` and `step in` work?

## Student Dinner
For dinner, all of the full-time current students who were attending CppCon were invited to a dinner with other students and some famous people from C++ community (like Bjarne S.). I had a lot of fun! I met some other students and learned about the kinds of things they do with C++ and it was very interesting.

## Grill the Committee
After the dinner there was 'Grill the Committee' session. Even though up until this point I haven't really kept up with what is going on in the C++ community or different proposals, I learned about some ongoing concerns that people have or some areas of C++ that are of great interest/concern to many.

# Day 2 - Tuesday, Sept 25, 2018

## Kate Gregory - What Do We Mean When We Say Nothing At All?
This talk poached the reader to think about what the presence of certain keywords in the code communicates to the readers and how to ensure that lack thereof is also meaningful.

This is a quote that I really liked from Kate -
> You should be writing your code as if your children will be maintaining it.

In other words - ensure you are communicating everything you want with the code you are writing. Kate gave lots of advice on how to communicate your intentions via different constructs.

#### [[fallthrough]]
Using `fallthrough` does not make a difference at runtime, but the compiler will complain if you misuse it.
#### on defaults
- Avoid defaults because not everyone knows it. Not using defaults allows you to communicate your intent better.
- Saves others time guessing if you have considered it
- **For nothing to mean something, in other places you have to make your intent *explicit***

#### on parameter passing
`const`, `&` convey the meaning about your API design (examples in the talk)

#### on traditional loops
When you have a *traditional loop*, is it because it's not touching some objects? If yes, well there are algorithms for that... There are lambdas too.
#### Importance of communicating
- Clear code communicates with future readers
- Shows them why you did something (your intent)
- "What does it mean when you make such choices"

**Ensure your nothing speaks volumes**.

#### Thoughts
I really like any talk that Kate gives. Communicating with future readers of your code is really important, and Kate gives lots of techniques for ensuring effective communication.

## Greg Law - More gdb and other Linux debugging wizardry
Soo I got a bit confused during this talk so my notes are just bullet points of some bits of information I understood and things I will look up in future

#### Intro
There are two main classes of debugging tools:
1. Checkers
  - Does my code do a bad thing, X, Y, Z? Examples include valgrind, address sanitizers, etc.
2. Debuggers

#### Signals
- When the program receives a signal, it's suspended and tracer(??) gets notified
- `gdb` might decide not to handle the signal
- `handle SIGSYS stop print pass` is how you can tell `gdb` to not handle certain signals

#### Misc
- Valgrind is a platform on top of which other checkers, e.g. memcheck, are built. It also has a remote debug server.
- There are different kind of sanitizers - address, memory, leak, etc...

#### Things to look up in detail
- ftrace - function tracer
- strace - traces all function calls of a process
- ltrace - dynamic calls of a process
- reverse-step in gdb??
- live recorder in gdb??

I know that \*trace are very useful tools to know about, but I just never happened to use them before. I think I used strace for something once, but that's it. I definitely need to look up all of those tools to see what kinds of things are possible to use them for.
#### Thoughts
I am interested in the things presented in this talk, so when I have more time I will definitely rewatch this.

## Richard Powell - Named Arguments
In this talk, Richard showed the process of turning an idea about C++ language extension into reality. This was one of my favorite live demos! Richard incrementally prototyped named arguments in C++ from scratch.
At first, he started with posing the question - what if we wanted to go from `foo(6)` to `foo(a=6)` in C++? How would we start? Well, what if we had a map with arguments and their names? Then we could extract arguments from the map and feed them to the function.

The high level steps are:
- **construct** the arguments
- **extract** the arguments
- **unpack** the arguments

I really liked the way he structured the presentation and live demo. It was not confusing at all, even though I didn't know hana boost library or some of the exact techniques that Richard used.

At the end of the talk, Richard emphasized that it's okay that this example is not production ready. The important thing that he wanted to demonstrate is how turn an idea into a product. Not everything can be production ready, but the important thing is **journey** and **learning things**. One of the things he left us with was "Find a question. Then ask yourself, how can you do this in/with C++? "

I found this talk to be very insightful on how to approach problems in C++. I learned a lot and I really liked that Richard emphasized the journey and learning things.


#### Things to look up
- hana boost library
- hana literals
- What does header only library mean? Is the code only located in the header? Is that it?

## #include_cpp dinner
Another cool thing happened - I got to go to a #include_cpp dinner. There were a lot of people from #include_cpp community. There was dinner and a panel discussion featuring prominent women from the C++ community. They discussed how they got started with C++, what challenges they faced and gave advice. The dinner was great - we ate good food and chatted with people at our table. I got to know some other women in C++ and what they work on. Then, the panel discussion began after dinner. I'm not sure how to describe it, but I teared up a lot and wanted to give everyone a hug. I'm so glad to have heard from all of those women. Hearing about their experiences made me aware that my experiences are not unique and it was helpful to hear their advice on dealing with various challenges they faced. I'm so grateful that they shared all of those things with us. I'm also very grateful that this dinner was organized, because it was definitely one of my favorite events during this week.

# Day 3 - Wednesday, Sept 26, 2018

## Patricia Aas - Software Vulnerabilities
Patricia's talk focused on software vulnerabilities. Some of the lessons I learned
- Don't depend on undefined behavior
- Sometimes compilers optimize away the `memset`
  - Can be an issue if you are depending on it to erase your passwords!!!
- Shellcode - piece of code. Today it is meant to represent the fact that you are able to execute something natively
- Don't take external strings as format strings. They might not supply enough args and printf will read whatever the next thing on stack is

Patricia also showed how to perform a buffer overflow attack. I couldn't help but notice how well organized the code examples were. I think everyone who wants to show code on their slides needs to follow Patricia's examples. She highlighted different parts of the assembly or C code that we needed to look at, and it made it easier to follow along and not get distracted by other lines of code!

Patricia also talked about X Things She Would Rather You Not Do to prevent certain vulnerabilities. I did not write them down because I was afraid I would not be able to explain them properly. So you will have to watch the talk :)

## Kate Gregory - Simplicity
I got to introduce Kate for her keynote! Whaat? How did that happen? On Tuesday morning, Jon Kalb has emailed me and said that he really liked my [blog post](TODO) that Bryce forwarded to him. He asked if I would like to introduce Kate for her keynote. I couldn't believe it! As I have previously mentioned, I am a huge fan of Kate, and I have watched a lot of her videos. So of course I said yes! Before I went on stage, Jon gave me some advice "Breathe. Smile. Speak slowly", which I definitely tried to follow. It was such an honor to introduce Kate! :')

Here is a list of lessons learned (but of course, please exercise your judgement):
- When you teach, start simple. Omit things like error checking in order to lesson the cognitive burden.
- Remember, encapsulation != obscuration.
- Simpler code is harder to write! It is not often faster, because to make it faster you have to know somethign about the language. E.g. `auto p` vs `auto p&`.
- Short function names! If you can't name it, it is probably several functions.
- No nesting, return from your function early. (Also, there was a lighting talk on Wednesday or Thursday called 'Shape of a program' by @JamesMcNellis dedicated to this topic alone. Highly entertaining and also useful.)
- Clean up in destructors. No one will forget to clean up, especially if they add a new `throw` statement somewhere in one of the functions.
- **Think about the future**. It might be easy now, but later it will confuse people.

## C++ Community Building BoF
This was a Birds of a Feather session. The goal was to discuss how to build a successfull C++ community. I learned a lot of things and tried to write all of them down.

#### Running meetups
If you would like to organize a meetup, here are some ideas for how to do so:
- Reach out to speakers in other cities, in case they are travelling. If they are visiting your city, politely ask if they would like to speak at your event.
- It's important not only to have talks but also discussions and have the meetup be a group and not just a service with talks.
- Have lighting talks
- What about organizing a book club for various C++ books/articles?
- Get people to showcase their projects.
- What about reviewing resumes and giving people some feedback?
- Sometimes have activities that allow everyone to break up into smaller groups
- Ensure diversity of topics. E.g. if you find yourself mostly presenting talks about debuggers, maybe think about presenting something about graphics in C++. Or add some non-technical talks.

#### Sponsorship
How should you talk to a company when you would like their sponsorship?
- Tell them what they will get in return
  - e.g. you can provide them with 2 mins at the beginning of each talk, or distribute their swag, etc
- Tell them concrete things that you will need
  - e.g. pizza and printed flyers
- Maybe look for sponsorships from companies who hire C++ developers, because they will have more incentive to help you

#### Voluntering
How do you get volunteers to help you with your meetup?
- Split up and rotate roles between people.
- Can assign different people to find speakers.
- Ask for specific things to get done
  - e.g. we need someone to order pizza, receive the delivery and setup the pizzas
- You have to let go and not micro-manage people!
- Very important - appreciate volunteers - people are helping you in their free time, for free.

## Serge Guelton - C++ in Elvenland
Another really cool talk I wish I could understand but it went over my head :( That's okay though! I wrote down things I was confused about and I can read up on them later, and rewatch the talk.

- Symbol tables in ELF
- Symbol demangling
- Shrinking existing libraries
- UND in symbol table
- `nm`
- `readelf`
- `objdump`
- `objcopy`

## Lighting Talks
Lighting talks are such a great idea. @michaelcaisse is a very talented and super hilarious host.

One thing I have written down from the talks that I would like to look up is `std::basic_string`. Someone presented a lighting talk on using it instead of a vector. I'm intrigued.
# Day 4 - Thursday, Sept 27, 2018

## Herb Sutter - Thoughts on a More Powerful And Simpler C++
This was a long talk, but my notes are succint because in the middle of it there was a demo. I really like the way the demo was done. It got the point across as one wants a demo to do, but without the panics that everything might crash and not work. I thought this talk was well presented, and even though I have not heard of meta classes before, Herb explained them well and I was able to understand their purpose and why they are a Good Thing. Below are some notes I took.

When we add new things to the language, it is to
1. Make user code simpler
2. Remove edge cases, e.g. lifetimes
3. Discourage certain things

How do we know which features represent C++. Or to be more clear, what is C++? **
- Don't pay for what you don't use (0 overhead). Of course, you still have to pay for it when you use it.
- Leave no room for lower language (except for assembly).
- Backwards compatibility

What are properties of Good C++ Features?
- Express intent better
- Simplify C++ code (read, write, debug)
- Remove an exception to **
- Remove gotchas
- Help us deprecate something (e.g. `typedef` -> `using`)

## Jeff Trull - Liberating the Debugging Experience with the GDB Python API
This was one of my favorite talks!I was so blown away by this talk. I have previously heard of GDB's python APIs but I never got a chance to play around with them. The documentation was kind of scary to me and I wasn't really sure what is possible.

 Jeff's presentation was great! His live demos were well prepared and they were truly necessary in his talk. This talk not only taught us about Python APIs, but also taught us how to approach any obstacles in gdb and what is possible. I learned a lot of things and as soon as I have some time, I will be playing around with those APIs. I can't wait to build python hooks to make my debugging easier.

Here are 3 Very Cool Things You Can Do With GDB Python APIs.

#### 1. Improve Stack Traces
Frame decorators are filters and you can override them to add custom behavior. Jeff showed us how we could replace verbose `std` names with well known values.

#### 2. Easily Step To User Code
I don't know about you but when I'm stepping through code, sometimes I accidentally step into non-user code and It Is Very Annoying. Turns out, we can make it so that library code gets ignored using `gdb.Breakpoint`.
- Put commands that execute when a breakpoint is encountered
- Use `libclang` to find out semantic info about the code

#### 3. Finding Cycles
- Use valgrind, parse output of the monitor into a graph
- Use graph processing to find loops in your program.

#### Thoughts
- I can try to take notes about things I constantly get annoyed at when debugging and try to come up with a solution. Perhaps, if it is a common enough problem, I can share it with others and they will find it useful as well.

## My Lighting Talk

My lighting talk happened! During the day I took some time off to create my slides and @bunnyladame kindly looked over them after lunch. Since I did not have a lot of time to prepare, I couldn't talk about anything too technical so I thought I would share a cool feature of git that I learned this summer while interning at Mozilla - `git worktree`. Git worktrees helped me speed up my development workflow because it allowed me to have more than one branch checked out simultaneously without cloning the repository twice. The rough idea is that you have two working trees in different directories, and they share `.git` folder and all of the stashes and other metadata. My slides are [here](/assets/pdfs/Cppcon2018-Lighting-Talk.pdf). And I will share the link to the video when it comes out!

Before my talk @hankadusikova also looked over my slides and gave me thumbs up.

People were really supportive - some of them took photos of me and/or tweeted that they learned a new thing, which made me really happy! Turns out there were quite a few people who have not heard of git worktrees before, so I'm glad I was able to share something new with people.

P.S. I used [carbon.sh](https://carbon.now.sh) to produce beautiful 'screenshots' of my code.

# Day 5 - Friday, Sept 28, 2018
I was not feeling well in the first half of the day, so I was not able to take any notes. I'm definitely going to rewatch Mat Godbolt's "The Bits Between the Bits: How We Get to main()" talk.

# Summary

## Reflection
This part of the blog post is the hardest to write. I have a lot of Good Feelings about CppCon and I want to convey all of them. This has been one of the best experiences I have ever had. CppCon had a great atmosphere, and it was so easy to talk to people in the hallway. There was not a single moment in the conference when I felt alone or left out.

The talks were great and I come away with lots of things I want to learn more about. I'm feeling very inspired and motivated to explore new areas with C++ I have not explored before. There are some talks which have immediate impact on my work, like Jeff Trull's talk on GDB Python APIs, and there are talks which will affect my work and thinking in the long run; to name a few - Kate Gregory's "What Do We Mean When We Say Nothing At All?" and Richard Powell's "Named Arguments From Scratch in C++". There are also "C++ Community Building BoF" session and #include_cpp dinner  that taught me things I would have been unable to read about in the books.

I have also learned lots of things about C++ not only through talks, but through informal interactions and discussions with people in the hallways, over lunches and dinners. Someone at the conference told me they thought CppCon was life-changing for them, and I wholeheartedly agree. I have met such fantastic and kind people (a lot of them from #include_cpp) that it makes me incredibly sad that CppCon has an end to it. Everyone I hanged out with was so supportive, encouraging and wholesome. They tried to introduce me to new people, explained things patiently when I didn't know something and taught me new things about how to be a better human being. I feel incredibly lucky to have met all these wonderful people. I am graduating soon and as I begin the next stage of my life I'm happy to know that I am a part of such a great supportive community of people who share my interest in C++ and other things.

## Other Random Good Things That Happened To Me In No Particular Order
- Sunny weather in Bellevue
- Someone told me if I wanted to submit a proposal, they could help me edit/write the paper
- Sushi buffet
- Dumplings at Din Tai Fung

## Thank You
I'm going to echo some of the things I said on my Twitter. I'm so grateful to Women in Tech Fund, #include_cpp and 43 people who donated to gofundme for giving me the opportunity to attend CppCon. I also want to thank all the organizators and volunteers of CppCon! And I want to thank everyone who has been kind to me - I hope we cross paths at CppCons in future.
