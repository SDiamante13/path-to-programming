---
title: "Micro-designs: Wrapper"
date: 2022-07-05T15:55:21-04:00
tags: ["design", "OO"]
featured_image: ""
description: ""
draft: true
canonicalUrl: "https://www.path-to-programming.tech/posts/wrappers-design/"
---

Don't mock what you own
Better flexibility
Imagine having to go every axios is when some other http client comes about

https://www.thecodedself.com/The-Difference-Between-an-Adapter-and-a-Wrapper/

https://www.scaler.com/topics/java/wrapper-classes-in-java/
A wrapper encapsulates and hides the complexity of other code. The most common use of a wrapper is in the Facade pattern. Third-party code can be hard to use due to the fact that the exposed interface is made to accommodate many use cases. When you are only concerned about a subset of the features or the exposed interface, or you find that using the library is hard or tedious, then what you need is to wrap it in a simpler, more constrained interface.

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Random.html





Micro Designs: The Wrapper Class

Today we will explore a design called the wrapper class. There are several different situations where you can use a wrapper class.

When working with external libraries it is usually a good idea to create a Wrapper class.

Use a wrapper to avoid mocking what you don't own. When I want to control time I usually create a Wrapper.



Benefits:



Less shotgun surgery when the time comes to change your library



Easy to test



You can build the interface you wish you had

Facade Pattern



Show example of don't mock what you don't own (unusual spending)



First Class Collections. Primitive obsession fixes..

This uses wrapper class in a way.

