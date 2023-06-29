---
layout: post
title: "Clojure read-string"
date: 2023-06-26
---

In my TicTacToe game, I need to store previous games in a database so that they can be played later.
The object that I store a game as look something like:

```
{:date "Thu Jun 26 12:30:26 EDT 2023"
 :board [\_ \_ \_ \_ \_ \_ \_ \_ \_]
 :gamemode {:mode :pvc :difficulty :hard}}
 ```

Of course if we stored a pvp game, then we would not need the `:difficulty` part of `:gamemode`. But this is the
general structure.

A problem arises when trying to read in the `:board` and `:gamemode` because it reads them in as strings
when we want them to be a vector and map respectively.

So the internal data structure after reading in from the database might look like:

```
{:date "Thu Jun 26 12:30:26 EDT 2023"
 :board "[\\_ \\_ \\_ \\_ \\_ \\_ \\_ \\_ \\_]"
 :gamemode "{:mode :pvc :difficulty :hard}"}
 ```

This is where `read-string` comes in.

I can just call `read-string` on the board or gamemode and it will convert it to the correct type with
data intact.

As an example:
```clojure
(def obj {:date "Thu Jun 26 12:30:26 EDT 2023"
          :board "[\\_ \\_ \\_ \\_ \\_ \\_ \\_ \\_ \\_]"
          :gamemode "{:mode :pvc :difficulty :hard}"})

(read-string (:board obj))
; => [\_ \_ \_ \_ \_ \_ \_ \_ \_]

(read-string (:gamemode obj))
; => {:mode :pvc :difficulty :hard}
```