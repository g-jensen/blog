---
layout: post
title: "Parsing Rewrite"
date: 2023-07-28
---

Previously, I had a very poor setup for parsing HTTP messages. Parsing the start-line and headers was easy
enough, but parsing the body is where I made an error. Thus far, my HttpParser just read the body 
until the end of the InputStream because that's all it needed to do for my tests. Once I started testing Socket
connections, it became apparent that my current strategy of parsing the body was not going to work. This
is because Socket input and output streams don't close until the socket closes, so my body-parser would
simply block forever. The way around this is the use of the Content-Length header. 

If an HTTP message body is
to be parsed, there must be a Content-Length header (or Transfer-Encoding). Given that I would need to
make substantial changes to my HttpParser, I opted to take the opportunity to rewrite the class.

With my current setup, if there is no Content-Length header, I don't even try to parse a body. And if there is a Content-Length header, I only
read that much from the body. Which solves my blocking problem.