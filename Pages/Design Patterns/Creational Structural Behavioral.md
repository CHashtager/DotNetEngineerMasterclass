# Creational / Structural / Behavioral

- **Creational Patterns:** Provide ways to create objects while hiding the creation logic, rather than instantiating objects directly.
- Factory Method, Abstract Factory, Builder, Singleton
  - **Factory Method:** Defines an interface for creating an object, but lets subclasses alter the type of objects that will be created.
  - **Abstract Factory:** Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
  - **Builder:** Allows the construction of complex objects step by step. It separates the construction of a complex object from its representation so that the same construction process can create different representations.
  - **Singleton:** Ensures a class has only one instance, and provides a global point of access to it.
- **Structural Patterns:** Describe ways to compose objects
- Facade, Proxy, Decorator, Composite, Adapter, Flyweight, Bridge
  - **Facade:** Provides a simplified interface to a complex system of classes, library, or framework, making it easier to use.
  - **Proxy:** Provides a placeholder for another object to control access to it. This could be for the purpose of lazy initialization, access control, logging, monitoring, etc.
  - **Decorator:** Allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.
  - **Composite:** Composes objects into tree structures to represent part-whole hierarchies. It lets clients treat individual objects and compositions of objects uniformly.
  - **Adapter:** Allows objects with incompatible interfaces to collaborate.
  - **Flyweight:** Reduces the cost of creating and manipulating a large number of similar objects.
  - **Bridge:** Decouples an abstraction from its implementation so that the two can vary independently.
- **Behavioral Patterns:** Handle communication between objects
- Strategy, Template Method, Visitor, Chain of Responsibility, Mediator, State, Observer
  - **Strategy:** Defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.
  - **Template Method:** Defines the skeleton of an algorithm in the superclass but lets subclasses override specific steps of the algorithm without changing its structure.
  - **Visitor:** Lets you add further operations to objects without having to modify them.
  - **Chain of Responsibility:** Passes the request along a chain of handlers. Upon receiving a request, each handler decides either to process the request or to pass it to the next handler in the chain.
  - **Mediator:** Reduces coupling between classes by providing a central point of communication between them.
  - **State:** Allows an object to alter its behavior when its internal state changes. The object will appear to change its class.
  - **Observer:** Defines a dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.