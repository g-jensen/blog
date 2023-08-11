---
layout: post
title: "Cljs & Speclj"
date: 2023-08-09
---

Speclj, the Clojure testing framework I am using, also works with ClojureScript. This may surprise you
since ClojureScript doesn't exactly "run". It simply transpiles to Javascript. 

Well, to get testing working, I used Michael Whatcott's [cljs-sample-project](https://github.com/mdwhatcott/cljs-sample-project).
This includes a `runner` that handles everything, but what I think is really cool is how it works.
The ClojureScript is transpiled to Javascript. The tests then run inside a
[PhantomJS](https://phantomjs.org/) instance to output in the console. PhantomJS is a program that
simulates vanilla Javascript running in the terminal. I just found that this was a cool way to connect
multiple technologies to make a cohesive tool.