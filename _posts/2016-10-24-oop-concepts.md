---
layout: post
title: Object-oriented programming concepts
tags:
  - oop
---

## An object-oriented language definition

A language supports object-oriented programming if it has:
  
  - Encapsulation
  - Polymorphism
  - Inheritance

## Encapsulation

Encapsulation is the process of bundling things into a container. For example, a procedure is the container for many code statements, and a class is the container holding data and methods. Encapsulation helps to create boundaries between groups of things (or containers.)

<!--break-->

Using encapsulation on class level should be guided by the [single-responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). When packing data and methods into a class, the class reponsibility should be considered carefully so that the bundled data and methods match the responsibility, as we don't want a class to have multiple responsibilities. 

## Information hiding

Information hiding is the process of hiding design decisions or implementation details of one part of a program from the rest of the program. Thus, information hiding enables modifying one part of a program without affecting the others.

Information hiding is usually used together with encapsulation. For example, after encapsulation is used to bundle data and methods into a class, information hiding can then be used to hide specific implementation details of the class from the others.

It should be noted that in some contexts, encapsulation is also referred to as information hiding.

## Abstraction

Abstraction is the process of stripping inessential details from an object and keeping only the essential details distinguishing the object from others. Determining which parts of an object are essential is dependend on the perspective of the users of the object. Abstraction sometimes also means the result from stripping inessential details and keeping only essential details of an object.

Abstraction is a key technique to manage complexity since it helps to ignore unnecessary details and focuses solely on relevant details.

Because abstraction involves removing unnecessary details, it is usually used with information hiding.

## Inheritance

Inheritance is the ability to define a class based on an existing class. The defined class is then called subclass, whereas the existing class is called superclass. The subclass can access the code in the superclass if the code is designed to be inheritable. 

Inheritance might be used when a new class wants to reuse, customize, or extend existing code, or it might also be used to enable polymorphism.

Inheritance is also referred to as _is-a_ relationship meaning that an object of the subclass is substitutable for that of the superclass.

## Polymorphism

Polymorphism in OO language refers to [subtyping](https://en.wikipedia.org/wiki/Subtyping), a variant of [type polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science)). With polymorphism, an object of type `T` can [substitute](https://en.wikipedia.org/wiki/Liskov_substitution_principle) for another object of type `S` if `S` is higher than `T` in their type hierarchy. In other words, polymorphism enables dynamic binding via inheritance.

Due to polymorphism, the outcome of invoking an object's method is dependent on the dynamic type of the object, not its static type.

## Delegation

Delegation is when an object invokes a method of another object and the _self_ parameter within the context of the invoked method points to the invoking object. There are two forms of delegations: explicit and implicit. In the former, the invoking object explicitly passes itself as an argument to the invoked method, whereas in the latter, the invoked method is able to obtain a reference to the invoking object by itself and so the explicit passing of the invoking object is not needed. For example, in Java, if an object calls a method in its superclass, the method can reference the object via the keyword `this`.

## Forwarding (or Consultation)

Forwarding is similar to delegation in that it also occurs when an object invokes a method of another object but is different in that the _self_ parameter within the context of the invoked method points to the _invoked_ object.

Due to their similarity, forwarding is sometimes informally refered to as delegation.

## Composition

Composition is when an object includes other objects as its fields. Composition is also referred to as _has-a_ relationship in that the enclosing object _has_ the other objects.

## Further readings

1. Chapter 5, Code complete
2. Section 2.3, Object oriented analysis and design with applications
3. [http://wiki.c2.com/?PolymorphismEncapsulationInheritancea](http://wiki.c2.com/?PolymorphismEncapsulationInheritance)
4. [http://www.tonymarston.co.uk/php-mysql/abstraction.txt](http://www.tonymarston.co.uk/php-mysql/abstraction.txt)
5. [http://wiki.c2.com/?ObjectOrientedForDummies](http://wiki.c2.com/?ObjectOrientedForDummies)
6. [http://wiki.c2.com/?EncapsulationDefinition](http://wiki.c2.com/?EncapsulationDefinition)
7. [http://wiki.c2.com/?InformationHiding](http://wiki.c2.com/?InformationHiding)
8. [http://www.javaworld.com/article/2075271/core-java/encapsulation-is-not-information-hiding.html](http://www.javaworld.com/article/2075271/core-java/encapsulation-is-not-information-hiding.html)
9. [http://wiki.c2.com/?EncapsulationIsNotInformationHiding](http://wiki.c2.com/?EncapsulationIsNotInformationHiding)
10. [Missing in Action: Information Hiding](http://www.stevemcconnell.com/ieeesoftware/bp02.htm)
11. [Revisiting information hiding](https://www.cs.cmu.edu/~ckaestne/pdf/ecoop11.pdf)
12. [http://www.joelonsoftware.com/articles/LeakyAbstractions.html](http://www.joelonsoftware.com/articles/LeakyAbstractions.html)
13. [https://en.wikipedia.org/wiki/Polymorphism_(computer_science)](https://en.wikipedia.org/wiki/Polymorphism_(computer_science))
14. [https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming)](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))
15. [https://en.wikipedia.org/wiki/Delegation_(object-oriented_programming)](https://en.wikipedia.org/wiki/Delegation_(object-oriented_programming))
16. [https://en.wikipedia.org/wiki/Forwarding_(object-oriented_programming)](https://en.wikipedia.org/wiki/Forwarding_(object-oriented_programming))
17. [http://wiki.c2.com/?DelegationAndConsultation](http://wiki.c2.com/?DelegationAndConsultation)
18. [https://en.wikipedia.org/wiki/Object_composition#Recursive_composition](https://en.wikipedia.org/wiki/Object_composition#Recursive_composition)
19. [https://en.wikipedia.org/wiki/Forwarding_(object-oriented_programming)](https://en.wikipedia.org/wiki/Forwarding_(object-oriented_programming))
