---
layout: post
title: "Destructuring in Clojure"
date: 2023-05-22
---
Destructuring in Clojure is a way to make passing sequences into functions cleaner. An example of this
can be seen if you want to just get the first two elements of a sequence.

```clojure
(defn add-first-two [[element1 element2]] 
  (+ element1 element2))
```
Which is nicer than doing something like:
```clojure
(defn add-first-two [s] 
  (+ (first s) (second s)))
```

You can also get the first two elements as well as the whole sequence like so:
```clojure
(defn add-first-two-and-last [[element1 element2 :as s]] 
  (+ element1 element2 (last s)))
```

or the sequence without the destructured elements (just an example)
```clojure
(defn add-first-three [[element1 element2 & s]]
  (+ element1 element2 (first s)))
```

In general destructuring is very useful when making a function do a specific operation on the first
few elements of a sequence.