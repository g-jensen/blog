---
layout: post
title: "TicTacToe File Persistence"
date: 2023-06-21
---
One task for my TicTacToe project is to implement file persistence. This will store a game in a file so that it
can be completed later. For now, no fancy database engine will be used. We will simply use text. Clojure comes with a
`read-string` function which will make this a lot less painful than it could be. To start, I will outline the 4 functions
needed to implement this file persistence. These functions are `initialize`, `fetch-all-games`, `update-game [date board game-mode]`, and
`delete-game [date]`. `initialize` will simply create the file if it is not already created. `fetch-all-games` will
return a list of every game stored in the database. `update-game` will change the state of a game or create a new game if
it doesn't exist already. And finally, `delete-game` will delete a game. This storage of these games is based on the date
in which they are started. In other words, the unique identifier for the games is the date. This system
allows for easy implementation of file persistence and even allows for further extension.