---
layout: post
title: "Multimethods"
date: 2023-06-16
---
Multimethods in Clojure are a way to dispatch function calls based on parameter value.

I use them in my TicTacToe program to easily create different difficulty levels when playing against
the computer.

Firstly, I use `defmulti` to create the multimethod with a dispatch function:
```clojure
(defmulti get-computer-move (fn [difficulty board] difficulty))
```

Here we're defining `get-computer-move` to be a function that takes in two parameters, `difficulty`
and `board`. We also define the dispatch function to simply return the difficulty. The dispatch function
will be how the multimethod determines which method to call.

Next, I define some methods:
```clojure
(defmethod get-computer-move :hard [_ board]
  #_(...calculate the best move))

(defmethod get-computer-move :medium [_ board]
  #_(...calculate an easier move))

(defmethod get-computer-move :easy [_ board]
  #_(...calculate an even easier move))
```

The parameter after `get-computer-move` is the key to which the multimethod will look to find a
match with the dispatch function. So if `difficulty` is `:hard`, then it will call the first method.