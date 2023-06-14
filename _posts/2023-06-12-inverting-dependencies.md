---
layout: post
title: "Inverting Dependencies"
date: 2023-06-12
---

In a personal project of mine, a game written in C++, I use a graphics library called [SFML](https://www.sfml-dev.org/)
to do all sorts of stuff like open a window or draw sprites. Throughout my time using SFML, I would
sometimes feel uncomfortable with the surplus of unused functions and direct library`#include`s
because I felt it took away from the modularity of my project. What if I switched to a different
graphics library? A complete rewrite would be necessary. 

Then I learned about the Dependency Inversion Principle. This led me to refactor my project in a way
that I think really increases the cleanliness of the code.

Previously, I had a Game class and I would just use the RenderWindow class supplied by SFML to manage
the window. Now, I have something that looks like this:

![inverting.png](https://raw.githubusercontent.com/g-jensen/blog/main/assets/inverting.png)

Where the Window class is actually an interface, and SFMLWindow merely implements the functions that
I need to use with a window with SFML. This way I depend on abstractions rather than concretions. I can also now
much more easily switch over to another graphics library because all I would have to do is add another
class that implements Window's methods.