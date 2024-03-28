# Dynamics

## Dynamic Code Generation

- Generating and executing code at runtime.
  - **Generating IL with `DynamicMethod`:** This allows for the creation of methods at runtime using IL (Intermediate Language). It's powerful for scenarios requiring high performance and dynamic behavior.
  - **Emitting Assemblies and Types:** The **`System.Reflection.Emit`** namespace provides classes that can be used to define and create new types, methods, and even entire assemblies at runtime.

## Dynamic Programming

- Dynamic Language Runtime and dynamic features in C#.

    The Dynamic Language Runtime (DLR) and **`dynamic`** keyword in C# simplify operations involving dynamic types.

  - **Dynamic Language Runtime (DLR):** Provides runtime services for dynamic languages and dynamic features in C#, enabling operations on objects whose types are not known until runtime.
  - **`ExpandoObject`:** A provided class that enables adding and removing members dynamically at runtime. It's useful for working with dynamically shaped data, such as JSON parsing results.
