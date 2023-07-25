---
layout: post
title: "Defining Symbols"
date: 2023-07-21
---

The latest feature that I implemented in my math language is the ability to define a symbol and store
a value in that symbol. To implement this, I first needed to define a scope. To do this, I made the `evaluate()`
function take in a scope as a parameter for every node. In this case, a scope is simply a map of strings to values.
I also had to create a special type of node: a `SymbolExpressionNode`. A `SymbolExpressionNode` has a name, and when
`evaluate()` is called on a `SymbolsExpressionNode`, it returns the value corresponding its name in the
scope map. With a working scope, I could now define symbols within that scope. Whenever the interpreter came across
`def`, it would add the next two parameters as a key and value respectively to the scope map. For example,
`def A 5` would add the key value pair `(A,5)` to the scope map. This way I can pass in the updated scope
map to every `evaluate()` call, and it will evaluate A to 5.