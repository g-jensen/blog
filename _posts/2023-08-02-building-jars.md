---
layout: post
title: "Building Jars"
date: 2023-08-02
---

IntelliJ and Java make it pretty easy to build a Java project into a `.jar` file. Once I did this with my
HTTP Server program, all I needed to do was import it into my Clojure TicTacToe Project.

With Leiningen, building a Clojure project to a `.jar` is also pretty easy, it's just one command. But since
I've recently switched to Deps, the Leiningen ways don't work. The Deps way didn't turn out to be that
bad, though. There are just a few steps.

To build to a `.jar` with Deps, I need a
`build.clj` file which defines how to build the project. A sample can be found [here](https://clojure.org/guides/tools_build#_compiled_uberjar_application_build)
It uses the `tools.build` library to customize the build. With a completed `build.clj` file, all that
is left is to add an alias to `deps.edn` to point to that build file like so: 

```
{:build {:deps {io.github.clojure/tools.build {:git/tag "TAG" :git/sha "SHA"}}
         :ns-default build}}
```