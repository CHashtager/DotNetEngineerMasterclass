# Generics

- **Constraints:** Restrictions on the types that can be used as generic arguments.
  - Examples include **`where T : class`** (reference type constraint), **`where T : struct`** (value type constraint), and **`where T : IComparable`** (interface constraint).

    ```csharp
    where T : base-class // Base-class constraint
    where T : interface    // Interface constraint
    where T : class  // Reference-type constraint
    where T : class?  // Nullable Reference-type constraint
    where T : struct  // Value-type constraint (excludes Nullable types)
    where T : unmanaged // Unmanaged constraint
    where T : new() // Parameterless constructor constraint
    where U : T // Naked type constraint
    where T : notnull // Non-nullable value type, or from C# 8
                      // a non-nullable reference type.
    ```

- **Covariance:** Allowing a more derived type than originally specified.
  - For example, if you have an **`IEnumerable<Derived>`**, you can assign it to an **`IEnumerable<Base>`** if **`IEnumerable<T>`** is covariant.
  - For instance, type `IFoo<T>` has a covariant T if the following is legal:

    ```csharp
      IFoo<string> s = ...;
      IFoo<object> b = s;
    ```

  - Interfaces and delegates permit covariant type parameters, but classes do not because a class can implement
    both Covariance and Contravariance interfaces
  - B[] can be cast to A[] if B subclasses A (and both are reference types)

    ```csharp
    Bear[] bears = new Bear[3];
    Animal[] animals = bears;  // OK
    ```

  - The downside of this reusability is that element assignments can fail at runtime:

    ```csharp
    animals[0] = new Camel(); // Runtime error
    ```

- **Contravariance:** Allowing a less derived type than originally specified.
  - If you have a delegate expecting a parameter of type **`Base`**, contravariance allows it to work with a more derived type.

    ```csharp
      public interface IPushable<in T> { void Push (T obj); }
      IPushable<Animal> animals = new Stack<Animal>();
      IPushable<Bear> bears = animals; // Legal
      bears.Push (new Bear());
    ```
