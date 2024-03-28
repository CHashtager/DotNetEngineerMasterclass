# OOP

Object-Oriented Programming

## Paradigm

- A programming paradigm centered around the concept of "objects," which are instances of classes.

### Class

- A class is a blueprint or template for creating objects in object-oriented programming. It defines the properties and behaviors that objects instantiated from the class will have.

### Abstract Class

- An abstract class is a class that cannot be instantiated on its own and may contain abstract methods. It serves as a blueprint for other classes but is meant to be subclassed.

### Interface

- An interface is a collection of method signatures without implementation. Classes can implement interfaces to provide specific behavior, achieving multiple inheritance.

### Object

- An object is an instance of a class, created from the blueprint defined by the class. It encapsulates data and behavior.

### Difference Between a Class and an Object

- A class is a blueprint or template, while an object is an instance created from that template. In simpler terms, a class defines what an object will be, and an object is the actual instance of that definition.

### Differences Between an Abstract Class and an Interface

- An abstract class can have both abstract and non-abstract methods, while an interface contains only abstract methods.
- A class can extend only one abstract class, but it can implement multiple interfaces.
- An abstract class can have constructors, fields, and properties, while an interface cannot.

### Access Specifiers

- Access specifiers determine the visibility or accessibility of class members (methods, properties, fields) in object-oriented programming. Common specifiers include public, private, protected, and internal.

### Static Class

- A static class is a class that cannot be instantiated, and its members are accessed directly using the class name. It is often used for utility or helper functions.

### Static Method

- A static method belongs to the class rather than an instance of the class. It can be called without creating an instance of the class.

## Principles

### Inheritance

- A mechanism for creating a new class that is a modified version of an existing class.

### Encapsulation and Information Hiding

- **Encapsulation:** Bundling data and methods that operate on the data within a single unit.
- **Information Hiding:** Restricting access to certain details of an object and revealing only what is necessary.

### Method Hiding and Overriding

- **Method Hiding:** Declaring a method in a subclass with the same name as a method in the superclass.
- **Method Overriding:** Providing a specific implementation for a method in the subclass that is already defined in the superclass.

### Abstraction

- **Data Abstraction:** Representing essential features without including the background details.
- **Procedural (Process, Control) Abstraction:** Representing a process or control without detailing its internal complexities.
- **Procedural Abstraction by Parameterization:** Utilizing parameters to make a procedure more versatile.
- **Procedural Abstraction by Specification:** Defining a procedure without specifying how it achieves its goal.

### Polymorphism

- The ability of a single function or method to work on different types of data.

### Ad hoc Polymorphism

- Providing multiple implementations of a function for different types or numbers of parameters.

### Overloading Polymorphism

- Defining multiple methods with the same name but different parameter types or numbers.

### Coercion Polymorphism

- Automatically converting data from one type to another.

### Universal Polymorphism

- The ability to process objects of various types through a common interface.

### Inclusion Polymorphism

- Treating objects of a derived class as objects of their base class.

### Parametric Polymorphism

- **Invariant Parametric Polymorphism:** Types are preserved without modification.
- **Covariant Parametric Polymorphism:** Preserves the ordering of types.
- **Contravariant Parametric Polymorphism:** Reverses the ordering of types.

### Dispatch

- The process of selecting which implementation of a polymorphic operation to invoke.

### Static Dispatch

- Resolving method calls at compile-time.

### Dynamic Dispatch

- Resolving method calls at runtime.

### Single Dynamic Dispatch

- Choosing a method based on the type of a single object.

### Multiple Dynamic Dispatch

- Choosing a method based on the types of multiple objects.
