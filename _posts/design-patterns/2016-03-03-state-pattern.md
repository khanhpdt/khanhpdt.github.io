---
layout: post
title: State pattern
tags: [design-patterns]
---

# Intent

- Allows an object to adjust its behavior based on its state.

# Structure

![state-pattern-structure]({{ site.url }}/assets/imgs/patterns/design-patterns/state/structure.png)

- The client is decoupled from the object states. It does not know about the states as well as the associations between the states and the object behaviors.
- The behaviors are now handled by the corresponding state objects.
- The state transition method can be centralized in the `Object` or distributed over the concrete states.
- The `Object` can also pass itself as an argument to the operations of the state objects. This helps the state objects to access the information in the `Object`.

# Applicability

This pattern can be used when:

- You want to modify the object's behavior at run-time depending on its state.
- You want to eliminate the duplications of the conditional clause on the object's states which scatter over different places.
- You want to emphasize the transitions between states.
- You want to emphasize the associations between states and behaviors.
- There appear to have a lot of logics around the object states, and the states can themselves transform to different states. In these cases, it'll be more convenient to make the states objects and move the logics inside the states.

# Risk

- Increasing number of classes, as each state is now a class itself.
- Increasing number of objects. But this risk can be reduced by reusing the same instance of the state (if possible).
- Complicates the code.

# Implementation

- See [github/State](https://github.com/khanhpdt/design-patterns/tree/master/src/main/java/org/khanhpdt/designpatterns/state) for an example.

# Reference

- State, GOF book
