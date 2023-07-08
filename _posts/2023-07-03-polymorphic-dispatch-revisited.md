---
layout: post
title: "Polymorphic Dispatch Revisited"
date: 2023-07-03
---

In a [previous post about polymorphic dispatch](https://gregjensen.dev/blog/2023/06/13/polymorphic-dispatch.html),
I outlined Clojure's `defprotocol` and `defrecord` as 'the' way to do polymorphic dispatch.

While `defprotocol` and `defrecord` are used for polymorphic dispatch, a much more common and simple
way to do it is with multimethods. I have a whole other post about multimethods [here](https://gregjensen.dev/blog/2023/06/16/multimethods.html).

In that post you can see that multimethods generally take less code and are nice because they work well
with maps. You can pass in a single object that maps to the dispatch value you want while also
carrying any other data needed for the calculation.
Using multimethods is also good because you aren't instantiating so many objects.

Overall, protocols and records/types are useful, but it's good to use maps and multimethods by default.
