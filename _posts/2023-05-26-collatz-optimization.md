---
layout: post
title: "Euler #14"
date: 2023-05-26
---
Euler #14 asks
```Which starting number, under one million, produces the longest Collatz sequence?```

The naive and relatively fast approach looks at follows:
```clojure
(defn next-collatz [n]
  (if (even? n)
    (quot n 2)
    (inc (* 3 n))))

(defn collatz-seq [n]
  (if (= n 1)
    [1]
    (cons n (lazy-seq (collatz-seq (next-collatz n))))))

(defn collatz-seq-count [n]
  (count (collatz-seq n)))

(defn euler-14 [n] 
  (apply max-key collatz-seq-count (range 1 n)))
```
It gets the job done and in reasonable time:
```clojure
(time (euler-14 1000000))
"Elapsed time: 3591.471 msecs"
=> 837799
```
But a pretty obvious optimization is to remember previous lengths of Collatz sequences so that it isn't
necessary to recompute the whole sequence. I tried going the `memoize` route for this, but the fact that
you need to check if a value has already been cached complicated the procedure.

Here is my messy, but quicker approach:
```clojure
(defn next-collatz [n]
  (if (even? n)
    (quot n 2)
    (inc (* 3 n))))

(defn collatz-seq [n]
  (if (= n 1)
    [1]
    (cons n (lazy-seq (collatz-seq (next-collatz n))))))

(defn collatz-seq-count [n map]
  (loop [m 1 val n]
    (cond
      (= val 1) m
      (contains? map val) (+ m (get map val))
      :else (recur (inc m) (next-collatz val)))))

(defn euler-14 [n]
  (loop [m 1 max-key 0 max-val 0 map {}]
    (if (>= m n)
      max-key
      (let [count (collatz-seq-count m map)]
          (recur (inc m) (if (> count max-val) m max-key) (max max-val count) (assoc map m count))))))
```
It shaves off about two seconds:
```clojure
(time (euler-14 1000000))
"Elapsed time: 916.799042 msecs"
=> 837799
```