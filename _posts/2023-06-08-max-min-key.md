---
layout: post
title: "min-key and max-key"
date: 2023-06-08
---

In programming, it is a common to want to obtain the absolute extrema of a list based on a function that takes
the values of the list.

For example in my traveling salesman program, I wanted the shortest path so the function is the length. An example of an
implementation of this in C would look something like:
```c
Path shortest-path (Path[] paths, size_t size) {    
    Path min_path = paths[0];
    double min_path_length = path_length(paths[0]);

    for (size_t i = 1; i < size; i++) {
        double possible_min = path_length(paths[i]);
        if (possible_min < min_path_length) {
            min_path_length = possible_min;
            min_path = paths[i];
        }
    }
    
    return min_path;
}
```

This is very messy because we need to keep track of two variables, `min_path` and `min_path_length`.

But Clojure gives us a quick and simple way to do this with `min-key`:
```clojure
(defn shortest-path [paths]
  (apply min-key path-length paths))
```
`path-length` is passed in as the function that `min-key` should sort by, so `min-key` returns the path that
had the minimum value when passed into `path-length`