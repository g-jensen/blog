---
layout: post
title: "TicTacToe UI Improvements"
date: 2023-07-11
---

In a [previous post](https://gregjensen.dev/blog/2023/06/29/tictactoe-menu.html), I showed my menu system
for my TicTacToe program that I am creating. My newest story requires me to allow the user to select
any board size greater than two. I chose to go about this by creating a counter corresponding with the
desired board size that the user can either increment or decrement. But my current system doesn't easily
allow for the creation of a counter, so what should I do? Well, since I'm using maps and
multimethods to dispatch the `ui-components`, I simply add `:type :menu` to my previously made components and
`:type :counter` to my new component. This way I can make a multimethod, `draw-components` that dispatches
based on `:type`. I can the use my previous method of drawing menus and put it under the `:menu` method
and draw the counter with the `:counter` implementation of the multimethod. Since the counter also updates
the state differently to the regular menu, I also created a multimethod called `update-ui` that also dispatched
based on `:type`. This way I can update and draw any type of ui component.