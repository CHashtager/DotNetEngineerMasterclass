# Various Aspects

## Local method

- A method defined inside another method's body.

## CLR behind the scene implementations

- The internal workings and optimizations of the Common Language Runtime.

## new versus override

- `new:` Creating a new member that hides a member from a base class.
- `override:` Implementing a method defined in a base class.

```csharp
public class BaseClass
{
  public virtual void Foo()
  {
    Console.WriteLine ("BaseClass.Foo");
  }
}

public class Overrider : BaseClass
{
  public override void Foo()
  {
    Console.WriteLine ("Overrider.Foo");
  }
}

public class Hider : BaseClass
{
  public new void Foo()
  {
    Console.WriteLine ("Hider.Foo");
  }
}

Overrider over = new Overrider();
BaseClass b1 = over;
over.Foo();             // Overrider.Foo
b1.Foo();               // Overrider.Foo

Hider h = new Hider();
BaseClass b2 = h;
h.Foo();                // Hider.Foo
b2.Foo();               // BaseClass.Foo

```

## Initialization order

- The sequence in which objects and their members are initialized.
    1. **Static Members:** Initialized first in the order they appear in the source code.
    2. **Instance Members:** Initialized next, also in the order they appear in the source code.
    3. **Constructor:** Runs after all fields are initialized.

## Boxing and unboxing

- **Boxing:** Converting a value type to a reference type.
  - The process of converting a value type (such as **`int`**, **`double`**, etc.) into a reference type object.
- **Unboxing:** Converting a boxed value type back to its original value type.
  - The reverse process of converting a boxed object back into its corresponding value type. Unboxing requires an explicit cast.

```csharp
int i = 3;
object boxed = i;
i = 5;
Console.WriteLine (boxed); // 3
```

## Struct

- A value type that typically represents a single, immutable value.

## Ref Structs

- Value types with certain restrictions on their use.

## Friend Assemblies

- Assemblies that can access each other's internal members.

## Interface implementations

- Implementing methods defined in an interface.
  - Implementing an interface obligates the class or struct to provide implementations for all of the interface's members.

## Enum Type-Safety Issues

- Potential issues related to the type safety of enums.
  - Casting an arbitrary integer to an enum type will compile, but it may result in an invalid value if the integer is not one of the defined enum values.

## Enumeration and Iterators

- Creating and using iterators in C#.

## The `Array` Class

- Working with arrays in C#.

## `Nullable<T>` Struct

- Representing nullable value types.

## Nullable Reference Types

- Enabling nullable reference types in C#.

## Extension Methods

- Adding methods to existing types without modifying them.

## Anonymous Types

- Creating types without explicitly defining them.

    ```csharp
    var anonymousType = new { Name = "John Doe", Age = 30 };
    Console.WriteLine($"Name: {anonymousType.Name}, Age: {anonymousType.Age}");
    ```

## Tuple and ValueTuple

- Representing ordered sets of elements.

    ```csharp
    (string Name, int Age) person = ("John Doe", 30);
    Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
    ```

## Patterns

- Different pattern-matching techniques.
  - **Property Patterns:** Check properties of an object.

    ```csharp
    if (obj is { Name: "John", Age: 30 }) { /*...*/ }
    ```

  - **Tuple Patterns:** Check multiple values simultaneously.

    ```csharp
    var point = (x: 0, y: 0);
    if (point is (0, 0)) { /*...*/ }
    ```

  - **Positional Patterns:** Destructure an object for pattern matching.

    ```csharp
    if (obj is Person(string name, int age)) { /*...*/ }
    ```

  - **`var` Patterns:** Catch-all pattern that binds a variable.

    ```csharp
    if (obj is var value) { /*...*/ }
    ```

  - **Constant Patterns:** Match an expression against a constant value.

    ```csharp
    if (obj is 5) { /*...*/ }
    ```

## Dynamic Binding

- Dynamically resolving types and members at runtime.

    ```csharp
    dynamic dynamicVar = 1;
    dynamicVar = dynamicVar + " some string";
    Console.WriteLine(dynamicVar); // Outputs: "1 some string"
    ```

## Unsafe Code and Pointers

- Writing code that bypasses C#'s safety checks.

    ```csharp
    unsafe
    {
        int var = 10;
        int* p = &var;
        Console.WriteLine($"Data is: {*p}");
    }
    ```

## Preprocessor Directives

- Conditional compilation based on directives.
  - **Conditional Attributes**

    ```csharp
    #if DEBUG
    Console.WriteLine("Debug mode");
    #else
    Console.WriteLine("Not in debug mode");
    #endif
    ```
