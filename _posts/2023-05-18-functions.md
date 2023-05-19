---
layout: post
title: "Functions"
date: 2023-05-18
---

While watching the Clean Code video on functions, I wrote down parts that I found most important:

When writing Clean Code, functions should
* Do one thing
  * This is part of the definition of Clean Code
  * Ensures that code is modular
* Be 4-6 lines long
  * Allows the reader to easily step through a function when debugging
  * Supports the idea that a function should do one thing
    * If a function is long, it is likely doing more than one thing
* Be extracted until there is nothing left to extract
  * A good way to tell if a function does one thing is to try to extract from it
  * Keeps functions short