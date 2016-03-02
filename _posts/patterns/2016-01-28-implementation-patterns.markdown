---
layout: post
title: Implementation Patterns
category: patterns
---

- Encapsulated collection (http://martinfowler.com/bliki/EncapsulatedCollection.html)

  > The key point with this is that you don't want to give clients direct access to the collection data structure itself - for if you do it allows clients to alter the supplier's data without the supplier being able to intervene.

# Book: Implementation patterns, Kent Beck

## Chapter 7: Behavior
- Main flow
  - Must be expressed in the clearest way. This does not mean that the minor flows are not important. It just means that the main flow must be the most visible one, so that readers know that it is the main processing of the code and the others are not as important.
  - The minor flows should not be written in a way that obscures the main flow. Exceptions and guard clauses can be used for these minor flows. Just remember not to let them get in the way of the main flow.

- Messages
  - Make it possible to modify the message receiver without affecting the sender.
  - Due to polymorphism, the message handling may vary at run-time.
  - Polymorphic messages are good for code extension because new message handling can be added without changing the existing handlings. However, porlymorphic messages are not good for studying code as the readers have to navigate to a lot of classes to understand a message. Sometimes it also makes debugging code become annoying as we have to know the exact receivers to be able to put breakpoints there.
  - Should always try to find an intention-revealing names for methods, because this helps the readers a lot when studying the code.

- Double dispatch
  - Messages are dispatched by two-level. After receiving the message, the first receiver will dispatch another message to the second receiver along with its information. The second receiver is the one that actually performs the job. See Visitor pattern for an application of this technique.

- Decomposing messages
  - If a message is too complicated (e.g., needs a long list of parameters), it is sometimes better to split the message into multiple ones, each of which handles an related aspects of the message.  

## Chapter 8: Methods
- Method name should be written from the client's perspective.

- Data and logic acting upon the data should be together.

- Complete constructor
  - If you want to impose required data on an object, introduce a constructor with the required data. The reverse also holds, which means that if a constructor has parameters, then it implies that the parameters are required for the object to function properly.

- Factory method
  - A (static) method used to create an instance of the class.
  - Should be used with care, as it implies that there's something special inside the method that a simple constructor would not suffice to do.
  - For example, factory methods should be used when the name is important, or when the return type is dynamic.

- Internal factory
  - Should use lazy initialization when the creation is complex. For example:
  <pre><code class="java">
	ComplexObject getComplexObject() {
		if (complexObj == null) {
			complexObj = doComplexComputation();
		}
		return complexObj;
	}
  </code></pre>

- Collection accessor method
  - If you happen to know that a bug can occur at runtime, try to eliminate it. The cost to debug such bug in production is expensive. For example, ``Collections.unmodifiableList(List)`` can cause exception if the clients try to modify the collection.
  - Try to reduce the accesses to the collections from the clients. This conforms to the rules "Minimize accessibility, Item 13" and "Minimize mutability, Item 15" in Effective Java.
  - Carefully analyze the clients to see if they really need access to the collections. If they just need to perform some simple operations on the collections, then we can just expose only those operations.

- Query method
  - If an object has a lot of logics dependent on the state of another object, it's likely that the logics are in a wrong place. This is similar to the smell of Feature Envy in Refactoring book.

- Equality method
  - equals() and hashCode() should be implemented together and should also operate on the same data. Similar to Item 9 in Effective Java. The reason is that equal objects must have the same hash code.

- Safe copy
  - Alias problem is when two different objects get control of the same other object without being aware of each other.
  - This pattern is only a palliative one, as it does not actually solve the alias problem, which is likely to be a design problem.

## Chapter 9: Collections
- Express one of the most fundamental variations in programming, the variation in cardinality (the other variation is in behavior)

- Fundamental issues about collections
  - Size
  - Order
  - Uniqueness
  - Performance

- Use the possibly simplest collection implementation first. Later we can change to more specialized implementation if needed.

- Some kinds of collections
  - Array
	 - Built-in feature in Java
	 - Most efficient
	 - Fixed size
  - Iterable
	 - Just to iterate
	 - Used with foreach loop
  - Collection
     - Simple operations: add, remove, search, count
  - List
	 - Orderred items
  - Set
	 - No duplicate
  - SortedSet
	 - Orderred by a comparator
	 - No duplicate

- Performance factors on choosing collection type:
  - Type of frequent operations
  - Collection size
  - Profiling (don't just guess)

- Avoid extending collections by inheritance (try to use delegation instead)
