Before going to analyzing how Java passes arguments around, let's differentiate the two concepts of argument and parameter which usually get mixed up with each
other. And this is what Oracle defines:

Parameters refers to the list of variables in a method declaration.
Arguments are the actual values that are passed in when the method is invoked.

Next, let's check what happens when we create an object in the following example:

[code language="java"]
Car car = new Car();
[/code]
Two things happen after the above construction statement:

An instance of type Car is created in the heap
A reference to that instance is created in the stack
That means, an instance of type Car created by the operator new and the reference car are two totally different things, but are related by a one-way connection, where car can be used to change the instance.It is helpful to think about this relationship as the one between the remote and the TV, where the remote can change what is shown on the TV and the TV can just sit there and be changed.

Now, let's get to the main topic: Argument passing in Java.

To illustrate how the passing mechanism works, we will look at two typical cases:

Arguments are normal class instances
Arguments are strings
The passing mechanism are going to be explained via examples, which is IMO a very effective way to explain programming concepts in general.

Arguments are normal class instances
[code language="java"]
private static void testInstancePassing() {
	Person aPerson = new Person("Bruce");
	System.out.println(aPerson.getName()); // Bruce

	changeName(aPerson);
	System.out.println(aPerson.getName()); // Carl -> the Person has changed

	changePerson(aPerson);
	System.out.println(aPerson.getName()); // Carl -> the Person has not changed
}

private static void changeName(Person aPerson) {
	// changes the Person object which the aPerson references to
	aPerson.setName("Carl");
}

private static void changePerson(Person aPerson) {
	// aPerson now points to a new Person
	aPerson = new Person("Draco");
	System.out.println(aPerson.getName()); // Draco
}
[/code]
The results in the snippet show that the thing passed to the method cannot
be the object itself (because otherwise the changePerson() method
would change the Person object already). However, that thing can
still change what is hold inside the object. Therefore, that thing must be the
reference to the object.

Another thing that we can observe from the results is that, even though the
changePerson() method does change the passed argument aPerson inside the method, the original aPerson in the testInstancePassing() method still points to the same object. This shows that what Java actually does is that it copies the value of the original aPerson and then passes the copy value to the method changePerson(). Therefore, we can conclude that the argument passing in Java is actually a pass-by-value passing mechanism. This also applies when the passed arguments are of primitive types.

Arguments are strings
[code language="java"]
private static void testStringPassing() {
    String aString = "hello";

    changeCase(aString);
    System.out.println(aString); // hello

    changeString(aString);
    System.out.println(aString); // hello
}

private static void changeCase(String aString) {
    String upper = aString.toUpperCase();
    System.out.println(upper); // HELLO
}

private static void changeString(String aString) {
    aString = "goodbye";
    System.out.println(aString); // goodbye
}
[/code]
The same rule applies here. That means, Java still passes String
arguments by value, which is confirmed by the result after the changeString() method. However, there is an obvious difference if we look at the result after the changeCase() method. We can see that the original aString still holds the string "hello", even though according to what we analyzed in the previous case, the object that aString references to is supposed to be changed inside the method changeCase().

The reason why the String object that aString references to has not changed is because String object is immutable in Java. What the statement String upper = aString.toUpperCase(); does inside the changeCase() method is that it creates a new String object, which holds the result of aString.toUpperCase(), and then it makes upper a reference to that new object. Therefore, the String
object that aString references to has been left untouched and thus has not changed.

The analyses of the two cases can be summarized by the following picture:

java_argument_passing

In conclusion, the argument passing in Java is a pass-by-value mechanism.

References:

https://docs.oracle.com/javase/tutorial/java/javaOO/arguments.html
Thinking in Java, 4th, Bruce Eckel