---
layout: post
title: Java 8 in action
tags: [java]
---

# Reference: Book Java 8 in action

## Chapter 1
- Java 8 new features
  - Streams API
  - Passing code to methods
  - Default methods in interfaces
- While collections are mostly about storing and accessing data, streams are mostly about how to perform computations on the data. Streams allows and encourages to process the data in parallel.

## Chapter 2
- Behavior parameterization by passing code (which performs the behavior) around
- Predicate: a function which returns a boolean value

## Chapter 3: Lambda expressions
- Functional interface
  - An interface with _exactly_ one abstract method. The inheriting methods (not from Object) also count. The signature of the abstract method is also called the function descriptor.
  - Because it's only required for a function interface to have exactly one method, the number of default methods in the interface does not matter.
- Lambda expression
  - An anonymous function which can be passed around
  - Syntax:
    (parameters) -> expression
	(parameter) -> { statements }
  - Used in the context of a functional interface, and must have the same signature as the function descriptor of the interface.
- Compile-time type checking
  - Also performed on lambda expresion by relying on the context in which lambda is used (i.e., the client code and the function descriptor)
  - Special case: If the lambda body has only one statement, then its return type is compatible to both void and the type of the statement result.
- Type inference
  - The types of the parameters in lambda can be inferred by the compiler, just like the type infererence in the diamond operator.
- If the lambda uses local variables that are not defined inside the lambda, the variables must be either declaratively or effectively _final_.
- Closure
  - Loosely speaking, closure is a programming mechanism in which functions can access and modify variables defined outside of their scopes
  - Lambda is different with Closure in that it can only access but are not allowed to modify local variables in the enclosing method.
- Method reference
  - Syntactic sugar for lambdas
  - Syntax
	TargetReference::methodName
  - Main types
   - Static method: Type::methodName
   - Instance method of a type: Type::methodName
   - Instance method of an object: object::methodName
   - Constructor: Type::new
  - Usually combined with other utility methods to make code more concise

## Chapter 4: Streams
- Streams
  - "A sequence of elements from a source that supports data processing operations"
  - Designed to provide a declarative way to process collections (like the way SQL processes records): you specify _what_ you want to achieve
  - Supports pipelining
- Streams vs. Collections
  - Lazily constructed, i.e., elements are computed on demand. This is opposed to conventional collections, which are eagerly constructed or their elements are computed before being added to the collections.
  - A stream can only be iterated _once_ during its life-time.
  - Internal iterations, rather than external iterations which are used on collections. This internal iteration encapsulates the iterating implementation from the client code, thus giving more flexibility in how the iteration is done.
- Stream operations
  - Intermediate operations that can be pipelined. These operations do not return any result and are actually performed only when a terminal operation is invoked. This enables the loop fusion techniques.
  - Terminal operations that terminate the pipeline, close the stream, and return values or void.
- Working with streams usually involves three pieces
  - A data source
  - Intermediate operations
  - Terminal operations

## Chapter 5: Working with streams
- Stream operations
  - Stateless
  - Stateful
- Short-circuiting: A computation terminates as soon as the result is found.

## Chapter 6: Collecting data
- Collectors
  - Implements Collector interface
  - Applies transforming operation on stream elements and then collects these transformed elements into a specified data structure to produce the desired output.
- Collect vs. Reduce
  - Reduce always creates a new value for each element when processed
  - Collect does not create new value, instead it acts directly on the element. Thus it can also modify the elements during the process.
- Main collector usages
  - Reducing and summarizing
  - Grouping
    - Also supports multi-level grouping
- Multi-level collector
  - Inner collector is passed as an argument of the outer collector. The inner collector will act upon the result of the outer collector.

## Chapter 9: Default methods
- Three kinds of compatibility in Java code
  - Binary
  - Source
  - Behavior
- Default methods
  - Start with the `default` modifier
  - Defined inside interface
   - Can have body
   - The implementations of the interface do not need to override.
- Typical usages
  - Optional methods in the interface hierarchy
  - Simulate multiple inheritance because a class can implement multiple interfaces
- Resolution rules when a class implement multiple interfaces which happen to have the same default methods
  - Methods in ordinary classes win
  - Methods in the most specific interface win
  - Otherwise, conflicts occur. One solution is to let the current class override the default methods and then explicitly call the overriding methods.

## Chapter 13: Thinking functionally
- Ideas from functional programming
  - Functions as first-class citizens (in Java 8, functions are equivalent to methods and lambdas)
  - Pure functions: functions cause no side-effects (or observable effects).
  - Declarative programming: focus on the what, not the how, i.e., specify the desireed result, not how it should be done to achieve the result
  - Referential transparency: A method always produces the same result for the same arguments, regardless of the context in which it is called. Thus referential-transparency methods can be characterized by their inputs and outputs.
- Pure functional programming vs. Functional-style programming
  - Pure functional programming: methods are pure functions, which do not alter state of their enclosing class as well as all other objects.
  - Functional-style programming: methods can change state of some objects, as long as these changes are not observable by the callers. For example, methods ony change their local variables, or they change the state of some object but also revert the change before terminating.

## Chapter 14: Functional programming techniques
- Functions
  - First-class citizens. Functions are treated as values, e.g., they can be passed around as arguments
  - No side-effect
  - Currying: a technique to reduce the number of parameters. For example, let say you have a legacy function with 4 parameters f(a,b,c,d), but for some reason you don't want to pass all 4 arguments everytime you call the function but only 2 at a time. The following code shows one way to do that
  <pre><code class="java">
  Integer f(a,b,c,d) {
	  // do something
  }

  void g(a,b) {
	  return (c,d) -> f(a,b,c,d);
  }

  // client code
  BiFunction<Integer, Integer, Integer> f12 = g(1,2);
  int c = 3; int d = 4;
  f12(c,d);
  </code></pre>
- Persistent data structures
  - Persisting data structures means that they are isolated and thus not affected by changes happenning around them.
  - One way to achieve persistent data structures is to clone the existing data structures and operate upon the clone. Because the operations are performed only at the creation time, it does not count that the data structures are altered.
- Lazy evaluation with streams
  - e.g., lazy evaluation of stream elements
- Pattern matching
- Memoization or caching

# Reference: Book Java 8 Lambdas, O'Reilly
