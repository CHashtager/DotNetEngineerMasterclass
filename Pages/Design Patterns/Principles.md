# Principles

- **SOLID:**
    1. **Single Responsibility Principle (SRP)**: Every module or class should have responsibility over a single part of the functionality provided by the software, and that responsibility should be entirely encapsulated by the class. This means a class should have only one reason to change.
    2. **Open/Closed Principle (OCP)**: Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. This means you should be able to add new functionality without changing the existing code.
    3. **Liskov Substitution Principle (LSP)**: Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program. Essentially, if class B is a subtype of class A, we should be able to replace A with B without disrupting the behavior of our program.
    4. **Interface Segregation Principle (ISP)**: No client should be forced to depend on methods it does not use. This principle suggests that multiple, specific client interfaces are better than one general-purpose interface.
    5. **Dependency Inversion Principle (DIP)**: High-level modules should not depend on low-level modules. Both should depend on abstractions. Additionally, abstractions should not depend on details; details should depend on abstractions. This principle aims at reducing dependencies amongst the code modules.
- **Dependency Inversion vs. Inversion of Control vs. Dependency Injection**
  - **Dependency Inversion** is the principle that high-level modules should not depend on low-level modules, but both should depend on abstractions.
  - **Inversion of Control (IoC)** is a broader concept that involves inverting the flow of control in a system. Instead of the caller controlling how and when to call a component, the component controls when it is called. This is often achieved through mechanisms such as callbacks, event handling, or dependency injection.
  - **Dependency Injection** is a pattern used to implement IoC, where the dependencies of a class are supplied by an external entity rather than instantiated directly within the class. This allows for more modular and testable code.
- **DRY (Don't Repeat Yourself):** Avoid code duplication
  - Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.
- **KISS (Keep It Simple, Stupid):** Simplicity is key
  - Advocates for simplicity in design. Complexity should be avoided, as simpler solutions are easier to maintain and understand.
- **YAGNI (You Ain't Gonna Need It):** Don't implement features prematurely
  - Encourages developers not to implement functionality until it's necessary. Premature implementation can lead to wasted time and effort on features that are never used.
- **Separation of Concerns:** Separate different responsibilities into distinct components
- **Least Knowledge:** Minimize knowledge between components
  - A component should not know about the internal details of other components. It should only communicate with its immediate friends, promoting loose coupling.
- **The Hollywood Principle:** Don't call us, we'll call you
  - This principle is related to IoC and tells components to "don't call us, we'll call you." It suggests that high-level components should not depend on the low-level components but rather be called by them.
- **Favor Composition over Inheritance:** Prefer object composition over class inheritance
  - This principle suggests that class functionality should be achieved through composed objects' behaviors (composition) rather than inherited from a base or parent class.
  - Composition offers more flexibility in designing systems.
- **Program to an Interface, not an Implementation:** Decouple abstraction from implementation
  - This principle advocates for coding against interface abstractions rather than concrete implementations. This promotes decoupling and enhances flexibility and maintainability.
