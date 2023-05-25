---
layout: post
title: "Combinatorics in Clojure"
date: 2023-05-24
---
Combinatorics functions are pretty satisfying to implement in Clojure because of its
functional paradigm. Here are some basic combinatorics functions that I implemented in Clojure:

Factorial:
```clojure
(defn factorial [n]
  (if (< n 2)
    1
    (*' n (factorial (dec n)))))
```

Combinations (What are the ways I can choose k elements from a list?):
```clojure
(defn cons-many [element elements]
  (map #(cons element %) elements))

(defn combinations [elements k]
  (cond
    (= k 0) '(())
    (= k (count elements)) (list elements)
    :else (concat
            (cons-many (first elements) (combinations (rest elements) (dec k)))
            (combinations (rest elements) k))))
```

Permutations (What are the ways I can rearrange the elements of a list?):
```clojure
(defn exclude-element [element elements]
  (filter #(not= element %) elements))

(defn permutations [elements]
  (if (< (count elements) 2)
    (list elements)
    (for [i elements
          j (permutations (exclude-element i elements))]
      (cons i j))))
```