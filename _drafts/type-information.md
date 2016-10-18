In Java, runtime type information (RTTI) is a mechanism that allows to check and use the type information at run time.

To perform RTTI, Java uses objects of a special class named Class. Each class in Java has a corresponding Class object, which is created when the class is compiled. These Class objects are stored in the .class files and contain the information about the classes they represent.

(As a side note, the .class files are also used to create instances of regular classes. Whenever a static member of a class is referenced, the Java Virtual Machine (JVM) uses a subsystem called class loader to locate the .class file of that class and then use the .class file to create an instance of that class.)

RTTI in Java has two basic forms:

Traditional RTTI
Reflection
The main difference between these two variations is that: traditional RTTI requires .class files to be loaded at compile time, whereas reflection at runtime.

To perform the traditional RTTI, there are three ways:

Using explicit type cast: to cast the class of an object to other class. The most common use is to downcast an object to a lower class in the class hierachy, e.g.,
[code language="java"]
public void castObj(Object obj) {
	// throw ClassCastException if obj is actually not a Shape instance
	Shape shape = (Shape)obj;
	// throw ClassCastException if shape is actually not a Circle instance
	// (e.g., a Square instance)
	Circle circle = (Circle)shape;
	// but upcast does not need RTTI
	Square square = new Square();
	shape = square;
}
[/code]
Using Class objects

With the Class object, it is possbile to acquire all the information about the whole hierarchy of the class that the Class object represents. See Class API for details.

To obtain the Class object, there are several ways:
Using Class.forName("fully_qualified_class_name")
Using class literal, e.g., Square.class
Using an instance of the class, e.g., square.getClass()
The first approach is actually not recommended because it requires to hardcode the name of the class and thus not type-checked at compile time. The second approach can always be used in place of the first one to provide a safer solution which is checked at compile time.

Using instanceof operator or isInstance() method

These two approaces are equivalent and both used to check if an object is an instance of some class, e.g.,
[code language="java"]
private static void testClass(Object obj) {
    if (obj instanceof Square) {
        System.out.println("found Square object");
    }
    if (Square.class.isInstance(obj)) {
        System.out.println("found Square object");
    }
}
[/code]
However, the instanceof operator can only be used with named type only, whereas the isInstance() method can be used with a Class object, which provides more flexibility as the Class can be passed around while the named type cannot.

Reflection is a general concept in computer science, which is defined on Wikipedia as:

Reflection is the ability of a computer program to examine (type introspection) and modify the structure and behavior (specifically the values, meta-data, properties and functions) of the program at runtime.

In other words, with reflection, we can not just read the type information but can also change that information at runtime.

In Java, reflection is supported by the java.lang.reflect library which contains the classes Field, Method, and Constructor. To use this library, we also need to acquire a Class object. See also Class API for details.

Although reflection is a powerful technique, it is recommended to use it judiciously and if possible avoid using it. According to Reflection tutorial, there are three concerns when using reflection:

Performance Overhead
Security Restrictions
Exposure of Internals
In conclusion, RTTI in Java provides a powerful technique which enables the ability to access and modify the type information at runtime. However, RTTI should be used indiscriminately, and should be replaced by porlymorphism when possible (for detailed discussion, see Item 53, Effective Java, 2nd, Joshua Bloch).

Useful materials:

Chapter "Type information", Thinking in Java, 4th, Bruce Eckel
http://docs.oracle.com/javase/tutorial/reflect/index.html
http://www.javaworld.com/article/2077015/java-se/take-an-in-depth-look-at-the-java-reflection-api.html
http://zeroturnaround.com/rebellabs/rebel-labs-tutorial-do-you-really-get-classloaders/
https://en.wikipedia.org/wiki/Reflection_(computer_programming)