---
layout: post
title: "Kata Progress"
date: 2023-07-14
---

My newest kata is the sorting algorithm kata. More specifically, it implements bubble sort. By the end
of the kata, the program consists of three functions:

```clojure
(defn sort-pair [[a b]]
  (if (< a b)
    [a b]
    [b a]))

(defn iteration [vec]
  (loop [vec vec output []]
    (if (< (count vec) 2)
      (concat output vec)
      (let [[x y] (sort-pair (take 2 vec))]
        (recur (cons y (drop 2 vec)) (conj output x))))))

(defn sort-vec [vec]
  (loop [vec vec]
    (let [iterated-vec (iteration vec)]
      (if (= vec iterated-vec)
        vec
        (recur iterated-vec)))))
```

`sort-pair` simply sorts a vector with two elements as the name implies, `iteration` performs an
iteration of bubble sort, and `sort-vec` sorts a vector by recursively performing an iteration of bubble sort
on it until the iteration does nothing.