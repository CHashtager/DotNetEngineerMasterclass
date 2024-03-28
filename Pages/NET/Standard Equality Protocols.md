# Standard Equality Protocols

- Implementing equality checks in C#.

## **`==` and `!=` Operators**

- **Usage**: For comparing two objects or values. By default, these operators check for reference equality for reference types and bit-wise equality for value types.
- **Customization**: You can overload these operators to provide custom equality logic for your types.

## **Virtual `object.Equals` Method**

- **Usage**: Provides a way to check for equality. By default, it checks for reference equality.
- **Overriding**: You can override this method in your classes to implement value-based equality logic.

## **Static `object.Equals` Method**

- **Usage**: A static method that determines if two objects are equal by calling the instance **`Equals`** method, handling **`null`** values gracefully.
- **Example**: **`bool areEqual = object.Equals(obj1, obj2);`**

## **Static `object.ReferenceEquals` Method**

- **Usage**: Used to determine if two object references refer to the same instance, ignoring any **`==`** operator overloads.
- **Example**: **`bool areSame = object.ReferenceEquals(obj1, obj2);`**

## **The `IEquatable<T>` Interface**

- **Usage**: Allows for type-safe equality checking and should be implemented by types to provide a strongly typed method for determining equality.
- **Benefit**: Avoids boxing for value types and provides a clear contract for equality.

## **When `Equals` and `==` are Not Equal**

- The **`==`** operator checks for reference equality by default but can be overloaded to perform value equality checks.
- The **`Equals`** method performs reference equality for reference types but is often overridden to implement value equality.

## **Overriding `GetHashCode`**

- When overriding **`Equals`**, you must also override **`GetHashCode`** to ensure that two objects considered equal have the same hash code. This is crucial for types used in hash-based collections like **`Dictionary<TKey, TValue>`** and **`HashSet<T>`**.

## **Overriding `Equals`**

- **Object-Level Override**: Override the **`Equals(object obj)`** method to provide custom equality logic that applies to all instances of the class.
- **Type-Specific Override**: Implement the **`IEquatable<T>`** interface and override the **`Equals(T obj)`** method to provide type-specific equality logic, improving performance and type safety.

## **Best Practices**

- Consistency between **`Equals`**, **`==`**, and **`GetHashCode`** is crucial. If two objects are considered equal (**`Equals`** returns **`true`** or **`==`** returns **`true`**), they must return the same hash code.
- Always override **`GetHashCode`** when overriding **`Equals`**.
- Consider implementing **`IEquatable<T>`** for types that are frequently compared for equality.
- Use **`ReferenceEquals`** to check for reference identity explicitly, especially within **`Equals`** implementations to handle self-references.
