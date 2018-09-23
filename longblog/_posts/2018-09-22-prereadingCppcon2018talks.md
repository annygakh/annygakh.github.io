---
layout: post
category: longblog
title: Pre-reading about and preparing for attending Cppcon2018 talks.
published: true
---
I needed to prepare for Cppcon and I decided to look at each talk and write down any thoughts I have for the ones I want to attend.

## Monday talks
#### 9:00 AM - Concepts: The Future of Generic Programming by Bjarne Stroustrup

#### 11:00 AM - The C++ Execution Model by Bryce Adelstein Lelbach (see in person)
I took Introduction to Computer Systems and Advanced Operating Systems courses at my university, where we studied how threads work - their interaction with each other, layout in memory and scheduling thereof by the OS - all in C. I'm not sure how different it will be in C++, but I'm excited for this talk anyway!
#### 11:00 AM - How to Teach C++ and Influence a Generation by  Christopher Di Bella (watch online)
This talk is happening at the same time as the one above, and, unfortunately, I don't think I will be able to attend this one. But I'm excited to watch it afterwards. This talk resonates with me because I consume a lot of educational resources - from books to online tutorials - and not all of them are of the same quality and it will be interesting to see what the speaker proposes to achieve teaching C++ in an effective manner.

#### 2:00 PM Secure Coding Best Practices: Your First Line Is The Last Line Of Defense by Matthew Butler (see in person)
From the talk description itself, this is what will be discussed
> * How hackers think and how they identify weaknesses in our systems.
> * How to identify hidden attack surfaces, attack vectors and vulnerabilities in critical systems.
> * Where the most common vulnerabilities in Modern and classic C++ are and how to avoid them.
> * Why avoiding parts of the language doesn't help.
> * Where we can trade off security for performance.

This all sounds so intriguing! There will even be a demo of a classic buffer overflow exploit. Long time ago I tried to read "Hacking: The Art of Exploitation" by Jon Erickson, but I gave up at the very beginning. Perhaps, this talk will inspire me to revisit the book. :)

#### 3:15 PM - How C++ Debuggers Work by Simon Brand (see in person)
Ahhhh!! I'm so excited for this talk! I don't know much about debuggers - I frequently use gdb or lldb for debugging my programs, but I always wondered how it works. A few weeks ago I even added 'Learn how debuggers work' to my list of goals (I keep track of things I would like to learn when I have more time) even before knowing about this talk.

Simon even has a tutorial series [here](https://blog.tartanllama.xyz/writing-a-linux-debugger-setup/) describing how to write a Linux debugger. After skimming his blog, I found [another post](https://blog.tartanllama.xyz/learning-cpp/) I need to give a thorough read. I definitely will come back to look at more of his posts.

#### 4:45 PM - Unwinding the Stack: Exploring How C++ Exceptions Work on Windows by James McNellis (see in person)
Even though I am not a Windows developer, I am still very curious to learn about the low level details of how C++ exceptions work.

#### 3:15 PM - Class template argument deduction in C++ 17 by Timur Doumler (watch online)
I  know nothing about CATD but very eager to learn more. `nuff said :)

#### Not a talk - 'Grill the Committee'
This will be a panel discussion with the leaders of the C++ standards committee who will be taking questions from the audience.

## Tuesday talks

#### 8:00 AM - minidumps: gdb-compatible, software controlled core dumps by Matthew Fleming
core dumps and gdb sounds like a lot of fun!

#### 9:00 PM - What Do We Mean When We Say Nothing At All by Kate Gregory
I have watched other Kate's talks in the past and I really enjoyed them. Her talks always give me food for thought and I find them very interesting.

#### 12:30 PM - Debuggers for Modern Applications: Performance and Static Analysis by Samy Al Bahra
Debuggers. `nuff said.

#### 2:00 PM - More gdb and other Linux debugging wizardry by Greg Law
Even without looking at the description I was already sold on this talk! From the talk description
> This talk will demonstrate some of the power of newer versions of GDB (Reverse debug, dynamic printf, amazing scriptability possibilities through Python), as well as some of the other Linux debugging tools at your disposal: ftrace, strace, ltrace, valgrind, rr, asan, and lots of very useful stuff in /proc.

ftrace! strace! ltrace!! Ahhhhh, sounds amazing!

#### 3:15 PM - RVO is Harder than it Looks: the story of -Wreturn-std-move by Arthur O'Dwyer
I'm excited to hear about how Arthur has created a diagnostic for the Clang compiler and how one can contribute to Clang.

#### 3:50 PM - Memory Tagging and how it improves C++ memory safety by Kostya Serebryany
Recently I have read `Delta Pointers: Buffer Overflow Checks Without the Checks` from EuroSys18 and it was my first time coming across pointer tagging. I wonder how different memory tagging is (I have not looked too much into the details).

#### 4:45 PM - Named Arguments in C++ from Scratch by Richard Powell
From my understanding of the description, we will learn how to extend the language using Hana, a library for metaprogramming, to allow support for named arguments. Very cool, indeed!

#### 8:30 PM - Lighting Talks
Not sure what they will be about, but excited nevertheless!

## Wednesday talks
Are you still reading this?

#### 9:00 AM - Fast Conversion From UTF-8 with C++, DFAs and SSE Intrinsics by Bob Steagall
I know very little about UTF-8 and UTF-16, so I am hoping to learn more about this.

#### 10:30 AM - Simplicity: not just for beginners by Kate Gregory
Kate will be talking about how to make your C+ + code simpler, something that everyone needs to lear
#### 12:30 PM - Mixing Managed and Unmanaged Code and Targeting Cross Platform Distributions
> Even though we love C++, we don’t live in a C++-only world. In this session, you will be given the opportunity to ask questions about the best way to build applications in C++, yet also make them accessible to clients who use managed code. There will also be experts to answer questions about best practices for building C++ so it may be utilized efficiently in a cross-platform environment.


#### 2:00 PM - Understanding Optimizers: Helping the Compiler Help You by Nir Friedman
Hoping to learn more about optimizations done by the compiler.
#### 4:45 PM - C++ in Elvenland by Serge Guelton
Serge will be talking about binary format ELF and how understanding it can help a C++ developer understand the whole compilation chain.

#### 8:30 PM - Optimizing Code Speed and SpaSwithchesce with build Time Switches
Compiler experts will be present to answer questions and engage in a discussion about compilers and linkers.

## Thursday talks

#### 9:00 AM - OOP is Dead, Long Live Data-oriented Design by Stoyan Nikolov
Data oriented design will be introduced, and from my understanding, there will be a case study using Chrome browser.

#### 10:30 AM - Thoughts on a More Powerful and Simpler C++ by Herb Sutter
It is 10:30 PM at the moment of writing this, and I might be too tired, but I can't summarize what this talk will be about. But! It seems interesting and I'm looking forward to it.
#### 2:00 PM - Building a C++ Reflection System in One Weekend Using Clang and LLVM by Arvid Gerstmann
> In this talk we'll go over the design and implementation of a
> runtime reflection system, demonstrating the use of Clang and the
> LLVM framework to craft custom C++ tools for your own needs.

Count me in!

#### 3:30 PM Liberating the Debugging Experience with the GDB and Python API by Jeff Trull
Debuggers are cool, and often they have python APIs, which is extra cool because you can build your own custom tools using those APIs. So exciting!!

#### 8:30 PM - Lighting Talks
:)

## Friday talks

#### 9:00 AM - Debug C++ Without Running by Anastasiia Kazakova
Anastasia is from jetbrains, and I have previously heard an episode of Cppcast where they have interviewed her. I also use CLion a lot, so I'm very interested in attending this talk to learn more about their solutions to various problems they encounter while building their IDE.
#### 10:30 AM - The Bits Between the Bits: How We Get to main() by Matt Godbolt
Ahh!!!
> When you run your C++ code, have you ever considered how the linker, loader, operating system, C and C++ runtime all work so hard to get everything set up for you to start running your code in main()?

Can't wait for this! I am always so curious, and in my Introduction to Computer Systems course we might have done something like this with C, but I have forgotten it now, and it would be great to see what happens before main() in C++.
#### 1:30 PM - Clangd: architecture of a scalable C++ language server by Ilya Biryukov
A former colleague of mine recommended that I attend this talk, so I think I will do so! Even though I have not heard of LSP before. The mention of C++ text editors piqued my interest, because I'm very interested in how IDEs and text editors like vim are designed, and a while ago, I tried to develop my own vim-like text editor, as an exercise to learn more of C++.
#### 2:45 Spectre: Secrets, Side-Channels, Sandboxes and Security by Chandler Carruth
This talk will discuss different kinds of attacks.
#### 4:45 Closing Panel: Spectre
This panel will consist of several security experts.

## Final thoughts
Wow! I did not realize how much work it is to go through the entire schedule and write down my thoughts for each talk I would like to attend. I can't believe how many talks there will be, and I am so excited! At the same time, I am also so pleased to see that there are at least 15/20 mins between almost all of the talks. I am also very excited to see that in the evenings, around 8 PM, there are regularly scheduled lighting talks. I hope to spend most of my evenings attending those.





