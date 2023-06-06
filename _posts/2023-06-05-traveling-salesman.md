---
layout: post
title: "Traveling Salesman"
date: 2023-06-05
---
The Traveling Salesman problem, my latest kata, asks: `given a list of points, what is the shortest path to visit every point and return to the first point?`

My solution was to simply check every permutation of the points and pick the path with the shortest length. This strategy is exceptionally slow. O(n!) slow, in fact. My main function in Clojure boiled down to the following:
```clojure
(def shortest-path [points]
  (apply min-key #(path-length (conj % (first points))) (permutations points)))
```

When doing some research on the problem, I found an optimized algorithm that runs in O(n^2 * 2^n) and even a quantum algorithm that runs in O(1.728^n).

But one interesting approximation of the solution I found uses ant colonies. Real ants create paths by taking into account trail pheromones, and the algorithm uses a probabilistic approach by simulating how ant colonies choose paths between food sources. Essentially, a large amount of ants are sent out to explore many routes and each ant will choose the next node based on the distance and amount of virtual pheromone on the node. This simulation gives a decent and quick approximation for the Traveling Salesman problem.
