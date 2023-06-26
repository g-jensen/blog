---
layout: post
title: "Quil Mouse Clicks"
date: 2023-06-22
---
In my Traveling Salesman point picker, I am using the graphics library Quil to display graphics. Quil also
handles user input like key presses and mouse clicks. Previously, I was using a bad method of managing mouse
presses. Every frame, I was simply checking if the mouse was clicked, and if it was then I would do what I want.
This caused some problems because for reasons like framerate, some mouse clicks would not be registered
because they were not done close enough to the call of the `update` function. But there is an easier way.
Quil actually comes with a `mouse-clicked` event bind that event works with `fun-mode`. You can define what
function you want to be called by adding `:mouse-clicked my-function` to the parameters in the `defsketch`.
In `fun-mode` (functional mode), `my-function` should take in two parameters, one for the current state and one
for information about what button has been pressed and where. Whatever is returned from the function is also
used as the new state for the next frame.