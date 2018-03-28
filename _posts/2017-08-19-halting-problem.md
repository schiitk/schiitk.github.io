---
layout: post
title: "The Halting Problem"
date: 2017-08-19 00:22:00 +0530
excerpt: Turing Machines, the Halting Problem and glimpses of computability theory
author: Chetan Vuppulury
homepage : http://plebhathnowebsite.com/
minutes : 1
comments: true
---
Why should we study the Halting Problem?
Because a lot of really practical problems are the halting problem in disguise. A solution to them solves the halting problem. Here are some examples.
* You want a compiler that finds the fastest possible machine code for a given program. Actually the halting problem.
* You have JavaScript, with some variables at a high-security level, and some at a low-security level. You want to make sure that an attacker can't get at the high-security information. This is also just the halting problem.
* You have a parser for your programming language. You change it, but you want to make sure it still parses all the programs it used to. Actually the halting problem.
* You have an anti-virus program, and you want to see if it ever executes a malicious instruction. Actually just the halting problem.
See more on the CS-StackExchange [here](https://cs.stackexchange.com/a/32853).

The speaker introduced foundations of computability theory and recursive functions through this talk, finally building up to the halting problem.