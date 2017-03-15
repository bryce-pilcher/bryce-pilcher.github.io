---
layout: post
title: "Race Detection for Web Applications"
date: 2017-03-14
category: review
---

The paper [Race Detection for Web Applications](http://researcher.watson.ibm.com/researcher/files/us-msridhar/pldi12-wr.pdf) details the establishment of a happens-before relation for the web and the creation of a tool called WebRacer which takes advantage of the newly specified happens-before relation.

#### Problem
Concurrency.  Actions in programs running in a non-sequential manner is tough.  We as programmers have a hard time wrapping our head around exactly how an execution could go and can often miss race conditions.  

This problem is extended when we believe we are working in a mostly serialized environment, but are in the middle of an asynchronous environment.  Welcome to the web!  How can things become asynchronous without our knowledge? When we are working with a language that is loaded and interpreted at runtime.  There is no pre-compile-make-sure-everything-is-ready part of the web.  It gets close, don’t get me wrong, but it is asynchronous in nature.  

How then do we detect race conditions? And how do we define memory accesses in an environment that does have standard memory access?

#### Solution
The authors took great care to design a happens-before relation that follows web specifications and confirms to much of the major browsers implementations.  This happens-before relation is a framework that allows for a system to be implemented for the detection of race conditions in/on various web pages.  A great understanding of JavaScript’s specifications was required to setup the happens-before relations properly.  

Built upon this happens-before relation is just the system mentioned above, WebRacer.  WebRacer was implemented and instrumented by the authors to detect race conditions on websites.  A large number of bugs were discovered across the four categories (HTML, Function, Variable, and EventDispatch) that WebRacer looked at, but in some categories, particularly HTML and Function, the benign races detected were quite high.  This bring into question the effectiveness of this happens-before relation in these categories.  However, in EventDispatch, 83 of the 91 discovered races were harmful, a significant number that proves usefulness. 

#### The cool part
I believe that the use of the tool, WebRacer, on the number of public sites which they used it is an awesome performance test.  Getting around the obfuscated code and the lack of understanding in the websites design did not seem to be much a hindrance for this project.  

#### The flaw
I thought everything about the happens-before relation and WebRacer was very well explained.  I also thought they were fair with the limitations of their tool.

#### Ideas for future work
One of the motivations mentioned was that hidden JavaScript crashes can mask more serious problems, including the possibility of leaving objects in an inconsistent state.  I think this would be an interesting area for which to develop automated detection techniques.

Additionally, implementing the rest of the happens-before relation that was not included in WebRacer, is another future work possibility.

I would also be interested to see this tool run on government websites to determine their performance and/or security.  
