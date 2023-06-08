---
layout: post
title: "A Discrete Cantor Set"
date: 2023-06-07
---

A couple of months ago, I participated in the [IUPUI Highschool Mathematics Contest](https://science.iupui.edu/math/about/math-contest/index.html)
which was an experience that I really enjoyed. The theme was fractals, and contestants had two and a half months to solve 4 problems and
write an essay on the theme.

Problem 3, the problem that I found the most interesting, defines a function, `f: N -> N` (which just means `f` maps
nonnegative integers to nonnegative integers) with the following recursive properties:
* `f(0) = 1`
* `f(3n) = f(n)`
* `f(3n+1) = 0`
* `f(3n+2) = f(n)`

The problem then asks for the sum of `f(n)` over all integers `0 <= n <= 10^23`.

Here is a table of some small values for `f(n)`:

| `n`    | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|--------|---|---|---|---|---|---|---|---|---|
| `f(n)` | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 |

I won't spoil the beautiful answer, but I will say that my strategy for solving this problem was to look
at patterns in the sum of `f(n)` up to `3^k` and then use another pattern to make that useful for
finding the sum up to `10^23`

The real beauty is in the question, though. This is because the simple recursive definition of `f` is strongly linked
to a popular fractal (probably could've guessed that by the theme of the contest), known as the [Cantor Set](https://en.wikipedia.org/wiki/Cantor_set). 
The Cantor Set relates to the set of real numbers on the interval [0,1] and is constructed by recursively removing
the middle third of the interval(s). This problem can essentially be thought of as a discrete version of this
Cantor Set since it is only defined for the natural numbers.