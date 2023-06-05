---
layout: post
title: "Defprotocol"
date: 2023-06-02
---
`defprotocol` is Clojure's strategy for allowing dynamic polymorphism.

When using `defprotocol`, implementations of functions are not included.
```clojure
(defprotocol GameObject 
  (update-obj [this]))
```
Here, we create a protocol named `GameObject` and define a function `update-obj` but do not implement it.

Now we can create types that derive from `GameObject`:
```clojure
(deftype Player [] 
  GameObject
  (update-obj [this] "update player stuff"))

(deftype LightSource []
  GameObject
  (update-obj [this] "update light source stuff"))
```
We can now call `update-obj` polymorphically on `Player` or `LightSource`
```clojure
(update-obj (Player.))      ;=> "update player stuff"
(update-obj (LightSource.)) ;=> "update light source stuff"
```