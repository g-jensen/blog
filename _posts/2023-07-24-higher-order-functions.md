---
layout: post
title: "Higher Order Functions"
date: 2023-07-24
---

The final feature that implemented in my math language is the ability to call higher order functions. 
The functions that I implemented are `sum` and `product` which will take in a range and a single-variable function, `f`. 
`sum` will add up each value in the range plugged in to `f`. For example, `sum 2 5 sin` equates to `sin(2) + sin(3) + sin(4) + sin(5)`.
`product` does the same as sum but for multiplication. The implementations of these function are pretty simple: just a for loop.
And to get the function that is passed into the higher-order function, I just look it up in the scope of defined functions.