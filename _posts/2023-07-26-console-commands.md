---
layout: post
title: "Console Commands"
date: 2023-07-26
---

When implementing command line options for my HTTP server project, I could have just put a couple
if statements and called it a day since I only need two options: `-p <port>` and `-r <rootDirectory>`.
I decided against this and instead, I made a nice abstraction for adding options in general. In a separate package called commandparser,
I created a class that makes it possible to simply call `addCommand(name,defaultValue)` to add a command which
will be added to a hashmap and updated once `parseTokens(tokens)` is called. It is also possible to add
a `usage` message to a command with the `addUsage(command,message)` method. This makes it so that if there is an
error when parsing the tokens, it will throw a BadUsageException with the usage message for the token that it found the error. 
For example, if I `addCommand("-p",80)` and then `addUsage("-p","-p <port>")`, if there is an error parsing the port (like if the value given is not a number),
then it will throw and error with the message `"Bad Usage of -p. Usage: -p <port>"`. The same goes for the root directory. This
way it will be easy to add more commands in the future if needed.