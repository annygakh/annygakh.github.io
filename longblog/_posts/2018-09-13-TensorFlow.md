---
layout: post
title: CPSC 448 - Understanding TensorFlow
category: longblog
published: true
---

The research project I am contributing to requires me to understand how TensorFlow works. Specifically, how distributed TensorFlow works. I have never worked with TensorFlow before, so at first, I need to understand how normal TensorFlow works, before understanding how it distributes tasks to more than one worker.

I have already taken a Machine Learning course in school, so I was able to get started with TensorFlow guides right away, without having to read up about it (which I will recommend for those who have not!).


### Steps to understanding TensorFlow with the focus on distributed aspect
1. TensorFlow's Programming Model
- Low level introduction to TensorFlow operations https://www.tensorflow.org/guide/low_level_intro
- A lecture recording from Stanford. Watch until ~19min mark. https://youtu.be/PicxU81owCs?t=5m
2. Distributed TensorFlow
- A talk from TensorFlow Dev summit https://www.youtube.com/watch?v=la_M6bCV91M
- An example program https://www.tensorflow.org/deploy/distributed. I would recommend reading this and understanding why different parts of the code are needed. However, this tutorial only provides you with a skeleton of the code, and not a complete program that is runnable out of the box, because you still need to write your own model. At this point, I still did not know how to create one, nor did I want to, because I just wanted to experiment deploying a TensorFlow cluster, without diving deep into creating models.
- This is a distributed TensorFlow program that someone wrote  https://github.com/ischlag/distributed-tensorflow-example. I followed this example to actually deploy a TensorFlow cluster, and see it in action.

Together, these resources were able to give me a high level overview of how TensorFlow works and how it distributes the tasks.

Below are some notes I took while watching Standford's lecture on TensorFlow.

![Image](/assets/images/IMG_6850.JPG)
![Image](/assets/images/IMG_6851.JPG)


