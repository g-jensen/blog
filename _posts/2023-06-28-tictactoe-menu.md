---
layout: post
title: "TicTacToe Menu"
date: 2023-06-28
---

In an attempt to make my TicTacToe menu system more testable and less fragile, I have all
the necessary behavior stored using multimethods and maps.

To save the state within the main menu, I create a multimethod named `next-state` which
takes in a `state` and an`input`

So the first couple menu elements looks like this:
```clojure
(defmulti next-state :state)

(defmethod next-state :default [state input]
  {:state :database})

(defmethod next-state :database [state input]
           (cond
             (= "1" input) (assoc state :database (FileDatabase. "games.txt") :state :load-type)
             (= "2" input) (assoc state :database (SQLDatabase. "games.db") :state :load-type)
             :else state))

(defmethod next-state :load-type [state input]
           (cond
             (= "1" input) (assoc state :load-type :new :state :board-size)
             (= "2" input) (assoc state :load-type :load :state :select-game)
             :else state))
```

This way we can keep calling `next-state` recursively and create an order. So something like
```clojure
(loop [state (menu/next-state {} nil)]
      (if (= :done (:state state))
        state
        (recur (menu/next-state state (read-line)))))
```

Would keep prompting the console for new state information in the order we specified above.

To get the ui components of a menu, I use more multimethods:
```clojure
(defmulti ui-components :state)

(defmethod ui-components :database [state]
  {:label "Database"
   :options ["1. File Database" "2. SQL Database"]})

(defmethod ui-components :load-type [state]
           {:label "Load Type"
            :options ["1. New Game" "2. Load Game"]})
```

This way, for a console game, I can just print the label and options while recurring through
the state like so:
```clojure
(loop [state (menu/next-state {} nil)]
    (if (= :done (:state state))
      state
      (do (println (:label (menu/ui-components state)))
          (println (str/join "\n" (:options (menu/ui-components state))))
          (recur (menu/next-state state (read-line))))))
```