# Events

- Mechanism for communication between objects.
- **Delegate:** Delegates are type-safe pointers to methods. They are the foundation of events in .NET. An event is declared in a class as a delegate type.
  - **Parameter Compatibility:** The parameters of the delegate define what arguments must be passed to the methods it points to.

    ```csharp
    delegate void StringAction(string s);
    class Test
    {
        static void Main()
        {
            StringAction sa = new StringAction(ActOnObject); sa("hello");
        }
        static void ActOnObject(object o) => Console.WriteLine(o); // hello
    }
    ```

  - **Return Type Compatibility:** The return type of the delegate specifies the return type of the methods it can point to.

    ```csharp
    delegate object ObjectRetriever();
    class Test
    {
        static void Main()
        {
            ObjectRetriever o = new ObjectRetriever(RetrieveString);
            object result = o();
            Console.WriteLine(result);  // hello
        }
        static string RetrieveString() => "hello";
    }
    ```

  - **Generic Delegate Type:** Generics can be used with delegates to define parameterized delegate types, making them more flexible and reusable. For example, **`Func<T, TResult>`** and **`Action<T>`** are built-in generic delegates.

    ```csharp
    delegate TResult Func<out TResult>();
    // allowing:
    Func<string> x = ...;
    Func<object> y = x;
    
    delegate void Action<in T> (T arg);
    // allowing:
    Action<object> x = ...;
    Action<string> y = x;
    ```
