---
layout: post
title: "Server Threading"
date: 2023-07-31
---

The final feature of my HTTP Server that I needed to implement is a `ping` resource. Whenever the ping
resource is requested, the server will wait one second before responding with the current time. If many
`ping` requests are sent in quick succession, they should all take exact one second to respond. The idea
being that it creates a simple way to test if the server supports multi-threading.

Up until this point, I had only tested my server responding to single requests. In fact, the way I had it
set up was that it would simply respond to the first request it got and then quit. So I needed to make
the server respond to multiple requests in its lifetime while also supporting multi-threading.

These two requirements were pretty similar because to even test if my server can respond to multiple requests, I would
have to run the server in a separate thread. The only hiccup I encountered when implementing multi-threading
was that I accidentally forgot to also make the test multithreaded, so my tests ran in sequence which made it seem like
my server was not supporting threading. Eventually I got everything working and had a finished product
to show at IPM.