---
layout: post
title: "Open-Closed Principle"
date: 2023-05-30
---
The Open-Closed Principle is very important to follow when writing Clean Code. Uncle Bob refers to the Open-Closed Principle as the moral center of software architecture. The "Open-Closed"
part of the name is saying that in software, modules should be <u>open for extension</u> but <u>closed for modification</u>.

But what do these phrases mean more specifically? "Open for extension" means that code should be organized in such a way
that new features can simply be plugged in. "Closed for modification" means that the implementation of these plug-ins
should not modify existing source-code. Essentially, this means that when adding a new feature, code should be added instead
of changed.

To adhere to the Open-Closed Principle, one must abstract and invert. Ugly switch statements or if-chains should
be converted to a single polymorphic method call. Dependencies should point to interfaces to allow modules
to be open for extension.

But know that adhering to the Open-Closed Principle perfectly is impossible. Customers will always find a way to want a feature that requires modification. And you should only try to predict changes that are similar to past changes.