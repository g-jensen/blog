---
layout: post
title: "SQL Persistence in Clojure"
date: 2023-06-27
---

Using SQLite for my TicTacToe game was surprisingly simple. It's very easy to add a package as a
dependency through Leiningen. I simply had to add 
```
[org.clojure/java.jdbc "0.7.8"]
[org.xerial/sqlite-jdbc "3.23.1"]
```

to my dependency list and everything worked. SQLite was even preinstalled on my computer.

Implementing the functions needed for my TicTacToe game was also simple with SQLite.

To start modifying the database, define an SQL database object:
```clojure
(def sql-db {:classname "org.sqlite.JDBC" :subprotocol "sqlite" :subname "games.db"})
```

Some examples of creating tables, selecting entries, and deleting entries look like so:
```clojure
(db-do-commands sql-db 
                "CREATE TABLE IF NOT EXISTS GAMES
                 (DATE text,
                 BOARD blob,
                 GAMEMODE blob)")

(query sql-db ["select * from games"])

(execute! sql-db ["DELETE FROM games WHERE date = ?" some-date])
```