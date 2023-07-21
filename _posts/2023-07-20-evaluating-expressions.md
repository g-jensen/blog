---
layout: post
title: "Evaluating Expressions"
date: 2023-07-20
---

Today, I created functionality to parse and evaluate prefix expressions in my [math language](https://gregjensen.dev/blog/2023/07/18/new-project.html).
To parse, I created an ExpressionParser class that only has one public method and a couple private ones.
The public method is `String[] getTokens(String input)` and it converts a string like `"(+ 23 9)"` 
into an array of strings like `["(","+","23","9",")"]`, this way it is easier to evaluate expressions
which is what I created the functionality for next. To evaluate expressions, I made a hierarchy of 
`ExpressionNode`s like so:

![class-diagram](https://raw.githubusercontent.com/g-jensen/blog/main/assets/ast.png)

Then, to construct the tree of nodes, I just loop through the tokens and create a new node based on
what the token is. When the tree is constructed, all I have to do to evaluate it is call `evaluate()` on
the root node.