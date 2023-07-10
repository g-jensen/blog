---
layout: post
title: "Immutability and Purity"
date: 2023-07-06
---

Two defining features of a functional programming language are immutability and purity. 

Immutability refers to data that is created during the runtime of the program.
Immutability means that once data is created, it cannot be altered. This means that to "change" data, one must create
new data that has the "changes" that they desire. If you are coming from a non-functional language, then
this idea fundamentally changes (get it) how you think about programming an algorithm. 

Purity refers specifically to functions. A pure function has no "side effects." This means that it doesn't
change any data or do anything that is outside the function. A pure function will do the same thing
100% of the time given the same parameters. This makes debugging function easy because all you ever need
to know about a given function is what's inside it. It also makes threading easy because functions will
never have side effects that may impact other threads.