---
layout: post
title: Command pattern
category: patterns
tags: command
---

# Intent

- Encapsulates a request _as_ an object.

# Structure

![command-pattern-structure]({{ site.url }}/assets/imgs/patterns/design-patterns/command/structure.png)

All information needed to carry out the request is encapsulated in the Command object. In other words, the Command objects contain the input data for the request and know how to handle the request.

The Command objects might handle the requests themselves or delegate the tasks to appropriate Receivers.

# Applicability

This pattern can be used when:

- You want to parameterize the request handling, because you can get different handlings by using different Command objects.
- You want to decouple the request invoker and the request handler. They are decoupled because they don't know about each other but only about the Command objects which act as intermediate objects between them.
- The time when the request is created and when it is handled is independent. For example, the time when a request is handled is determined by a queue manager, but the time when it is created is by a client. In this case, you should let the client create a Command object and pass it to the queue manager. Then, when the time comes, the queue manager will simply invoke the Command object to carry out the request.
- You want to support a set of related operations and you don't want to scatter them in different places. The most common case is to support both do() and undo() operations in a Command object.

# Reference

- Command, GOF book
- Command, Chaper 24, Design Patterns In Java
