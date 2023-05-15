---
layout: post
title: "Tail End Recursion"
date: 2023-05-10
---
In Clojure, there aren't really iterative loops. Instead, we can get
loop functionality through recursion.

The behavior of a simple `for` loop in C

```c
for (int i = 0; i < 10; i++) {
    ...
}
   ```

can be translated into a `loop` form in Clojure like so:

```clojure
(loop [i 0]
  (if (< i 10)
    (do (...)
        (recur (inc i)))))
```

The call to `recur` evaluates the second parameter of `loop` again with the
new specified `i` value

`recur` utilizes Tail End Recursion, which works by having `recur` be the last
call in the loop. This allows the recursion to essentially be treated like
a conventional loop as to not cause a stack overflow.

A simple use case can be seen in the implementation of the `factorial` function.

An implementation like this
```clojure
(defn factorial [n]
  (if (<= n 1)
    1
    (*' n (factorial (dec n)))))
   ```
has the possibility of blowing the stack, while an implementation like this
```clojure
(defn factorial-recur [n]
  (loop [n n acc 1]
    (if (<= n 1)
      acc
      (recur (dec n) (*' n acc)))))
```
does not.