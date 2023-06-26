---
layout: post
title: "TicTacToe SQL Persistence"
date: 2023-06-23
---
My latest task for my TicTacToe project is to implement SQL persistence (a database). 
SQL is a relational database management system. I have previously implemented a file persistence, and
since I adhered to the Open-Closed principle, adding SQL functionality is easy. I already have an interface
called `Database` and type called `FileDatabase` which implements the `initialize`, `fetch-all-games`, `update-game`, and
`delete-game` functions. So all I have to do is make another type called `SQLDatabase` and implement those function
and everything works perfectly. The fact that I did not have to modify existing code to add this feature
shows that I was adhering to the Open-Closed principle because my code was open for extension and closed for modification.