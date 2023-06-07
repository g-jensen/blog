---
layout: post
title: "Interface Segregation"
date: 2023-06-06
---

The Interface Segregation Principle (aka the ISP and the 'I' in SOLID) is strongly linked to the 
Single Responsibility Principle. Imagine a big class that does a lot of different things and therefore is
depended on by many other classes. Uncle Bob refers to this idea as a Fat Class. This is a blatant
violation of the Single Responsibility Principle because the Fat Class has many responsibilities. 
The existence of this Fat Class also makes it hard to independently deploy each module since they all depend on the Fat Class. And a system that is hard
to independently deploy is hard to independently develop because many different actors must change the Fat Class
to suit their needs. A way to fix this problem is to apply the Interface Segregation Principle. The bottom-line of
the ISP says to only allow modules to know what they NEED to know. This is done by creating an interface connecting
each class that depends on the Fat Class that contains only what the class needs from the Fat Class. This ensures that
each class only knows what they need to know from the Fat Class.