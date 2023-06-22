---
layout: post
title: "Square Root Construction"
date: 2023-06-20
---
Constructive Geometry or Straightedge and Compass Construction is a method of doing Mathematics with
only a compass and straightedge. The method was first used by ancient Greek mathematicians and even with
the limited tools, they were able to construct summations, ratios, and even square roots. The latter being
of particular interest. 

In Euclid's Elements, Euclid gives the construction of what is now known as the geometric mean of
two lengths `a` and `b`. Algebraically, the geometric mean of `a` and `b` equals `sqrt(a*b)`, so if we take
`b=1`, then using Euclid's construction, we can construct line of length `sqrt(a)` given a line of length
`a` and a unit length.

The construction goes as follows:

Construct a line AB

![sqrt1](https://raw.githubusercontent.com/g-jensen/blog/main/assets/sqrt1.png)

Add a point C such that BC is of unit length and AC is a line

![sqrt2](https://raw.githubusercontent.com/g-jensen/blog/main/assets/sqrt2.png)

Label D as the midpoint of AC

![sqrt3](https://raw.githubusercontent.com/g-jensen/blog/main/assets/sqrt3.png)

Draw a semi-circle centered at D with radius AD

![sqrt4](https://raw.githubusercontent.com/g-jensen/blog/main/assets/sqrt4.png)

Draw a line perpendicular to BC at B up to the semi-circle. Label the intersection of the new line and the semi-circle E.

![sqrt5](https://raw.githubusercontent.com/g-jensen/blog/main/assets/sqrt5.png)

The length BE is now sqrt(AB)