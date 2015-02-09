---
layout: post
title: Queues in software development
---

Queues are well known structures to most programmers. They are covered in most introductory courses on data structures, are a part of the standard libraries of most - if not all, languages that are widely used in the industry.

A queue is a structure that implements FIFO ordering on its constituent elements. The formal study of queues is called queuing theory. Apart from FIFO ordering, two other properties that are interesting are average waiting time and average length of the queue.

In a typical software development workflow, *tasks* flow through one of the following *activities*

1. Analysis
2. Development
3. QA
4. Acceptance test
5. Release

We can model the development workflow as a sequence of processes one for each *activity*. A *task* them becomes a unit of work that flows from one process to the next. People working on the task contribute *capacity* to the process. In a ideal scenario, each process would have exactly the right amount of capacity at exactly the right time to handle the tasks. But in most cases, the amount of capacity needed to perform the tasks is greater than the amount of capacity available. So inevitably, inputs to the processes get queued up. It is important to note that in a software development workflow, work not only flows forward, but also in certain cases, backward. If a bug is found by the QA, the task naturally moves back into the development queue.

![Software development queues](https://github.com/narainbalaji.github.io/raw/master/images/Queues.png "Software development queues")

This model of a software development workflow provides a structure with which we can reason about the following well known observations.

1. Estimating how long even a simple task would take is a hard problem
2. The latency and throughput of the development workflow is limited by slowest activity
3. Typing speed is not the bottleneck for any serious development process
4. Defects should be fixed before new development can take place
5. Knowledge silos are bad for the effectiveness of the process

Lets dissect them further.

### Estimating how long even a simple task would take is a hard problem

This is fairly obvious to prove using the queuing model. The total time for the completion of a task is the actual time spent working on the task, plus the time for which the task is waiting in one of the queues. We can at this point, go ahead and do a statistical analysis on the queues to calculate the average waiting times and there by calculate the total time; but one should question the usefulness of such an approach.

### The latency and throughput of the development workflow is limited by slowest activity

This is also a fairly obvious conclusion. If the QA process is limiting the throughput, it does not make sense to hire developers. But this is exactly what happens in many real world scenarios. The distinction becomes even more obscure when analysis is the limiting the throughput. Incompletely analyzed tasks are moved into the development queue which reduces the throughput of the development process and this leads to hiring more developers. All these underscore the importance of having structured feedback without which we could be solving all the wrong problems.

### Typing speed is not the bottleneck for any serious development process

The limiting factor in a software development process is not stationary. If one bottle neck is removed, another emerges. This is true for any queuing system as there exist at least one bottleneck in any queue. Too often, people engage in micro optimizations like choosing a language which has a less verbose syntax. They may or may not be the bottleneck of the system. Care should be taken to address the immediate bottlenecks prior to addressing potential ones down the line.

### Defects should be fixed before new development can take place

A version of a software system that has defects is usually not considered for shipment. Developing new features on top of a version that is known to have defects increase the probability of finding regression defects later on. This increases the total effort required to develop software.
