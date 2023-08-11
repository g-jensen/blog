---
layout: post
title: "Converting to Deps"
date: 2023-08-01
---

Thus far, I've been using [Leiningen](https://leiningen.org/) for all of my Clojure projects, but I recently
had to change that due to a new story requirement. With my finished Java HTTP server, I need to convert
that to a `.jar` and import it into my Clojure TicTacToe program to make a TicTacToe web server application.
The problem is, Leiningen doesn't have a way to import local jar files. So I had to convert my project to `deps`.

[Deps](https://clojure.org/guides/deps_and_cli) is Clojure's default project structure and dependency manager. It also happens to make it very easy
to import local jar files. To convert my project to deps, I needed to place Leiningen's `project.clj` with
Clojure's `deps.edn`. The `deps.edn` file has a different structure to `project.clj`, but the conversions are
relatively one-to-one.

With my new `dep.edn` file working, I can now reload my project as a Clojure Deps project and everything (including Intellij)
is working.