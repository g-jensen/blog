---
layout: post
title: "Abstracting Main"
date: 2023-06-01
---

While creating the game loop for a TicTacToe program, I noticed something interesting: my `main` function reads
like it could be the `main` function of any sort of board game. For example, without changing `main`, we could redefine all the functions that are called and create a
chess program.
```clojure
(defn -main [& args]
  (loop [board empty-board]
    (display-board board)
    (if (win? board)
      (display-winning-message board)
      (recur (play-move board (get-user-move))))))
```

This is the level of abstraction we are looking for when creating an architecture such that every module is a plugin.