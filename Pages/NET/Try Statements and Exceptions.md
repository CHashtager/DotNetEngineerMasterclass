# Try Statements and Exceptions

- Exception handling in C# using `try` blocks.
- **`try` Block:** Code that might throw an exception is placed inside a **`try`** block.
- **`catch` Block(s):** After a **`try`** block, one or more **`catch`** blocks can be used to specify handlers for different types of exceptions.
- **`finally` Block:** A **`finally`** block contains code that is executed after the **`try`** and **`catch`** blocks, regardless of whether an exception was thrown, and is typically used for cleanup code.
- **Exception Propagation:** If an exception is not caught in a **`catch`** block, it propagates up the call stack, looking for a matching **`catch`** block in the calling methods. If it reaches the main method without being caught, the program will terminate.
