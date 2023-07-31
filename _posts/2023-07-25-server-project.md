---
layout: post
title: "Server Project"
date: 2023-07-25
---

My latest project is to make an HTTP Server in Java from 'scratch' (not using an external library or the built-in http package).
This essentially means I have to manage raw data with sockets. Part of the acceptance criteria is to use
HTTP v1.1, so I will have to do some research on that protocol. Other than that, the requirements include being able to specify
port and root directory with console commands (which will be the first thing I work on) and adding a few pages. I will also need to implement sending
files with correct mime types. Finally, the server will have to be asynchronous to allow for multiple connections
at the same time and new connections while other connections are being processed.