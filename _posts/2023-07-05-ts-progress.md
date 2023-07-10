---
layout: post
title: "Traveling Salesman Progress"
date: 2023-07-05
---

I've made a lot of progress on my Traveling Salesman Kata recently. I still need to get it under 15 minutes, but I have
all the steps correct. Right now the way my tests are set up is that I test the different ways to make a path given n points.
So I start off with testing a 2 point path (a line) which is pretty basic. Then I test a 3 point path which has more tests
but is barely different. Once I get to a 4 point path I need to change a lot of stuff. And then I go on to 5 points for good measure.
I test each of these paths with different kinds of branches to make sure my algorithm takes the shortest path. One thing I might do
to speed up the kata is to test based on the branches rather than path size. For instance, my first test might be testing straight lines
of different sizes. And then I could test straight lines with a single branch. And then a double branch. This also could make my TDD smoother.