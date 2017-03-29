---
layout: post
title: "Probabilistic Replay with Execution Sketching on Multiprocessors"
date: 2017-03-29
category: review
---

This is a review of [PRES: Probabilistic Replay with Execution Sketching on Multiprocessors](http://www.cs.columbia.edu/~junfeng/12fa-e6121/papers/pres.pdf).  This goal of this study was todetermine a way to trace a programs execution in a production environment with low overhead and reliable replay.

#### Problem
Writing concurrent programs is tough, and often produces non-deterministic runs.  Any of these runs can lead to bugs in the execution because of atomicity violations or timing violations.  Tools are necessary to help solve this problem, but if not constructed correctly can make the bugs impossible to find.

Traditional debugging of stepping through the code in a concurrent program can sometimes cover up bugs and make them impossible to find. This is because it changes the timing of execution between threads.  Some tools randomize testing in an attempt to get bugs to present themselves, and these are often successful, but they lack a critical feature.  While they find bugs in concurrent programs, they don’t provide a way to replay the execution for the developer.  

Replaying the execution can be the key to understanding why globally a bug is manifesting rather than just the local interactions that is causing it.  It can also help developers discover unintended interleaving’s that may not be bugs, but just inefficient ways of working.  But, storing all the information about how a program ran can be an extreme amount of overhead and data.  

#### Solution
Provide developers with a tool that allows for production execution to be replayed in a way that does not incur massive overhead or large data stores.  This allows for developers to find bugs in production systems, vs their testing system.  Technology for repeatable environments has continued to get better, but everyone knows that you don’t know what the consumer/user will do and therefore production has its own set of challenges.  

The amount of information that it would take to completely replay a production system is staggering.  So the authors chose to use sketches of the production run that would capture important events and allow developers to replay close to how the production system actually ran. 

These sketches are fed into their Partial-Information based Replay (PI-Replay) which determines the unrecorded non-deterministic information.  This is done through exploration of the unrecorded space, often with multiple replay runs. Each time a replay is run, the feedback is incorporated in the next replay, so that their tool can effectively learn from itself. 

#### The cool part
I think it is awesome that they were able to use partial sketches with some kind of learning to help developers find bugs in production systems in a way that could be replayed.  

#### The flaw
I’m worried about the information that is being missed.  Is it possible that there is information there that could not be inferred from the sketch, but could lead to a bug? I would say almost surely there is a case that exists, therefore the better question might be how often does this occur.  But that question requires knowing or being able to approximate the set of bugs found or unfound. 

#### Ideas for future work
Perhaps store information in a sliding window of sorts.  For example store the past x time in a buffer and overwrite until a bug or error occurs, then use that information to help rebuild with the sketches.  

