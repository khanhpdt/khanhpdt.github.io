---
layout: post
title: Object-oriented design smells
excerpt: ""
categories: articles
tags: [oop, software-engineering]
---

These smells are the symptoms of a poor design. They should be cleaned up as soon as possible to stop them from spreading to other code.

## Rigidity

A design is rigid when changing code in one place causes changes to many other places.

Rigidity makes it expensive to change software because even a simple change can cause a lot of unexpected changes.

## Fragility

A design is fragile when changing code in one place can break code in other places that might not be related to the changed code at all.

Fragility makes it risky to change software because even a simple change can break code in the places that seem irrelevant to the changed code. It also makes the software less reliable, because the broken code due to the changes irrelevant to it might not be detected during development and thus can escape to the production environment.

## Immobility

A design is immobile when it is difficult to extract code in one part of the system to make it reuseable by other parts. The extraction is hard because the code to be extracted gets so entangled with other code that it cannot be extracted without affecting or including the other code.

Immobility causes code duplication because it hinders code reuse.

## Viscosity

A design is viscous when not-good solutions are more convenient than good ones. For example, given a problem and two possible solutions, one follows good practices and one does not. If the design makes it convenient to implement the latter, then the design is said to be viscous.

Because viscosity makes it easier to do the wrong things than to do the right things, it makes way for bad practices and thus progressively degrades the software quality.

## Needless complexity

Needless complexity is when a design is more complicated than it has to be. In other words, the system consists of redundant parts that do not contribute any value to the system functionality. Most of the time, those parts are the consequences of over-designing the solution to a problem at hand. For example, given a problem and two solutions, one is simple and one uses a sophisticated design pattern, if the latter is chosen simply because design patterns are known to be good practices or because of some unknown future requirements, then needless complexity has been introduced into the system.

Needless complexity makes code more complicated, less comprehensable, and less maintainable.

## Needless repetition

Needless repetition is when similar code or code in slightly different forms appear at different places. This is usually a consequence of immobility or simply of developer laziness.

Needless repetition makes code less maintainable, because if one piece of code is found as buggy, all of the similar pieces of code must be checked and fixed. This task can easily go out of hand in large systems.

## Opacity

Opacity emerges when it is difficult to understand the code.

Opacity hinders code maintainability because unreadable code takes more time to comprehend and sometimes can even be misunderstood.

# References

[1] Chapter 7, Agile Software Development, Principles, Patterns, and Practices, by Robert C. Martin
