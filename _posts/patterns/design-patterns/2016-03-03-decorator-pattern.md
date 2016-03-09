---
layout: post
title: Decorator pattern
tags: [software-engineering, design-patterns]
---

# Intent

- _Attaches_ additional responsibilities to an object dynamically and transparently.

# Structure

![decorator-pattern-structure]({{ site.url }}/assets/imgs/patterns/design-patterns/decorator/structure.png)

- The Decorator can also be an interface or abstract class.
- The Decorator conforms to the interface of its decorated Component to make it transparent to the clients of the Component.
- The Decorator keeps a reference to its decorated Component, so that it can attach additional responsibilities to the object at run-time.
- The Decorator does not alter the behaviors of its decorated object, but instead it attaches other behaviors to the object. In other words, the Decorator changes the /skin/ of an object, not its /guts/.

# Applicability

This pattern can be used when:

- You want to add new behaviors to before or after performing an operation of the decorated object.
- You want to introduce new behaviors but for some reasons you don't want to do that with inheritance.

# Risk

- Because the decorator extends its decorated type, it might be expensive to introduce new decorators if the decorated type is heavy-weight.
- Even thought the decorator extends its decorated type, the developers must be aware that the decorator does /not/ actually belong to the type hierarchy.

# Reference

- Decorator, GOF book
