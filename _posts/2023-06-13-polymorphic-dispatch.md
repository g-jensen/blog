---
layout: post
title: "Polymorphic Dispatch"
date: 2023-06-13
---

Polymorphic dispath is a way to call a function in a different way based on polymorphism. As an example, in my tictactoe game I have different game-modes: one for playing versus a player (`PvPGame`) and one for playing versus a computer (`PvCGame`). For all game-modes I want a `next-board` function to get the board with the next move played whether it may be from the user or from the the calculations of a computer. To do this, I made an interface (or protocol in Clojure) that houses a `next-board` function but does not implement it. Then, I created two the types PvPGame and PvCGame which inherit from GameMode and implemented `next-board` to my liking in both. This way in my main loop I can just call `next-board` regardless of the game-mode and polymorphic dispatch will make sure the right version of `next-board` is called.

My Clojure code for the protocol and types looks something like:
```clojure
(defprotocol GameMode
  (initial-board [this])
  (next-board [this board]))

(defrecord PvPGame []
  GameMode
  (next-board [this board]
    (play-move board (get-user-move))))

(defrecord PvCGame [player-character]
  GameMode
  (next-board [this board]
    (if (= player-character (player-to-move board))
      (play-move board (get-user-move))
      (play-move board (get-computer-move board)))))
```