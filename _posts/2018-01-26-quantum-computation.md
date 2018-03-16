---
layout: post
title: "Quanta on Quantum Computation"
date: 2018-01-22 00:22:00 +0530
excerpt: A badly written introduction to quantum complexity, because I am studying cool stuff and wanted to share it!
author: Sagnik Bhattacharya
homepage : https://sagnikb.github.io/
minutes : 8
comments: true
---
I am currently working on quantum complexity, with a working title of 'adversarial and polynomial methods in quantum query complexity'. If I come across something interesting, I plan to write on it as I guess it will sharpen my understanding of things, and maybe you, the reader, will find it cool too. This is meant as an introduction to the field itself.

Some background, then. Quantum computing can be said to have begun with Feynman thinking about the difficulty of simulating quantum systems on a classical computer, a difficulty arising out of the form of the governing equations. The question is that, if nature can achieve a (classical) computationally difficult task while evolving the world quantum mechanically, **can we harness the power to accomplish some tasks quicker than what we can do with classical computers?**

Now, David Deutsch came up with a problem in 1985, that he showed could be solved by quantum computers faster than any classical algorithm, (Deutsch's problem). This sparked some interest in the field, which increased when in 1992, Deutsch and Richard Jozsa gave a variation of the problem (Deutsch-Jozsa problem) and an algorithm to solve the problem that gave a stronger separation between classical and quantum computers (look at the appendix for more). This provided inspiration for some truly groundbreaking work later in the decade, with Shor's factoring algorithm and Grover's unstructured search algorithm, that provided clear separations between classical and quantum algorithms in problems of great practical importance.

The original question, however, has proved a little difficult to answer. Quantum algorithms like Grover's and Shor's, have been proposed that are faster than any known classical algorithm but we cannot just yet say that quantum computers are in general 'better' than classical computers. There are some questions that need to be answered first.

So, what are these questions?

First, the model. Many of the better known statements about 'running-time' of algorithms in classical computing depend on something called the Turing Machine model, but 'running-time' of quantum algorithms is different from the classical concept. Then, comparing between the two is like comparing apples and oranges. Not quite, though, because the oracle model can be used to prove certain lower bounds about the same problem in the Turing machine model, but we must at least be careful when making statements like 'Problem X is easier on a quantum computer than a classical computer'.

There's another model issue here. The laws of quantum mechanics forbid the perfect copying of an arbitrary quantum state (*the no-cloning theorem*), which is obviously not true classically (think of where these words came from![^1]). This therefore does place a restriction on the sort of things we are allowed to do. Also, quantum computing must be *reversible* in the absence of measurements, which is not necessary for classical computation, but this can be shown to not make much of a difference in the conclusions that can be drawn (I am skipping several details here though!). 

>**Aside #1 - The Turing Machine Model -** The Turing Machine model is an abstraction of what we mean by a classical computer running an algorithm. We endow a computer with infinite memory (certainly an abstraction!), in the form of a tape. This tape is segmented into boxes, and initially has the input on it, in the form of symbols in the boxes. It is fed to the Turing Machine, which then moves around on and manipulates symbols on the tape according to certain rules (the algorithm). When it stops, the tape is said to hold the output of the algorithm. This can be taken to be the most basic description of what an algorithm *means*. This was a revolutionary concept introduced by Alan Turing that changed the way we think about computation, and has wide ranging implications in computer science and mathematics. Running time of algorithms in this model is defined as the number of steps taken for the algorithm to stop. There are simplifications here, of course. For example, what if the algorithm doesn't stop? Since this isn't a course, I will pretend I didn't notice that!

>**Aside #2 - The Oracle Model -** The Query model is a different type of model of computation. Here, we don't assume the input to be given to the computer. However, the computer has access to an oracle, to which it can query the value of specific bits in the input. For example, if the input is a sequence of $$100$$ $$0$$'s and $$1$$'s, the computer may ask the value of the $$61$$<sup>st</sup> number in the sequence. This is, however, the classical version, and in the quantum version we can use a superposition of queries to 'query' multiple bits at the same time. Again, I have ignored subtleties ('Does that mean we can learn everything about all the input bits at once?').

Treating quantum computing in the Turing Machine model is difficult (proof by authority, bigger people think so!), so for the time being let's talk about classical computing also in the query model. Now can we compare classical and quantum computers? Let's first see an example.

Suppose there's a string of bits ($$0$$'s and $$1$$'s), of length $$n$$. You only know that there are just two possibilities, either all the bits are $$0$$ or there is just one $$1$$. You need to tell which one it is. Classically, we need to look at all the bits in the string, because we don't know where the $$1$$ is, which seems intuitively true [^2]. So we require about n queries to the oracle to answer the question (this can be mathematically proven). However, 'quantumly' (and this is Grover's algorithm), we can show that only about $$O(\sqrt{n})$$ queries are sufficient. In this case, then, we know that the quantum algorithm is better.

Now think of a hypothetical example, where we have an algorithm that does better than any known classical algorithm, but it hasn't been proven that there cannot exist a classical algorithm that can do better. Here, we cannot conclude that a quantum computer is better! This is an issue with a certain class of problems called the hidden subgroup problem, which is too technical to discuss here.

Another question can now arise : Can a quantum algorithm do better than Grover's search given the same problem? 

These are questions that **quantum complexity theory** basically seeks to answer. For example, given a problem (like the search problem mentioned above), what is a lower bound on the number of queries to an oracle that is required to solve the problem? An answer to a question like this allows us to determine in some sense 'the best we can do' to solve a given problem, and I find it pretty interesting! Answering this question for more and more problems is one of the ultimate aims for research in the area and I hope to make some contributions in the effort :D

#### Appendix - Deutsch's problem

The Deutsch's problem is the following.

>Given a function $$f : \{0,1\} \rightarrow \{0,1\}$$, and the promise that the function is either constant (same for both $$0$$ and $$1$$) or balanced ($$0$$ for $$1$$ and $$1$$ for $$0$$ or vice versa), tell which of the two possibilities is actually the case. Since we want the computation to be reversible and without any arbitrary copying, we consider a black-box that takes two inputs, $$x$$ and $$y$$, and outputs $$x$$ and $$f(x) \oplus y$$. Here $$\oplus$$ is the classical XOR ($$1$$ if $$x$$ and $$y$$ are different, $$0$$ otherwise). It can easily be checked that this is reversible (given the outputs, we can uniquely arrive at the inputs).

What is the quantum and classical solution for this problem? Classically, we need to use the black-box twice, but quantumly we can do it in one use! How? There's too much background that I need to get into to provide a sensible answer to that here, so I will take the easy way out and refer you [here](https://www.cse.iitk.ac.in/users/rmittal/prev_course/f17/reports/intro.pdf) for details. It is a link to the lecture notes from the very first lecture of a course (that I did!) on Quantum Computation by Dr Rajat Mittal (Computer Science and Engineering, IIT-Kanpur), and should be accessible to most readers!

***
[^1]: Shamelessly quoting the Bible of Quantum Computation, Nielsen-Chuang!
[^2]: For an example where even classically you do not need to look at everything, consider a problem where you are given a binary string of length n, and you know that it is *sorted*, ie all zeros appear at the beginning and all 1's appear at the end. You need to find the position of the first 1. Classically, you only require only $$O(\log{n})$$, using binary search.
