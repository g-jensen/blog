---
layout: post
title: "Parsing HTTP"
date: 2023-07-27
---

The Hypertext Transfer Protocol version 1.1 is defined by the structure of data being sent. There are precise
rules on how everything should be formatted. For example, an HTTP message has three parts: a start-line, a list of
field lines, and a body. Each of these parts are separated by a carriage return followed by a line feed.

The structures of each of these parts are detailed as well. A start-line has a method, request-target, and a version
which are all separated by single spaces. The field lines are a list of key-value pairs separates by a colon with an extra
newline signaling the end of the field lines. The body is simply the raw data being sent.

The definition of all of these
specific conventions makes it easy to implement a parsing algorithm and is why HTTP is so widely standardized.