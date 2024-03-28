# GC and Memory

## Garbage Collection and Memory Consumption

- Managing memory and garbage collection in C#.

### **Finalizers**

    Finalizers are special methods in a class that are called by the Garbage Collector when an object is being collected. They are used to release unmanaged resources that the object may have acquired during its lifetime, such as file handles or database connections. Finalizers are defined using the **`~ClassName()`** syntax.

- **Usage**: Rarely needed, as unmanaged resources are better managed through the **`IDisposable`** interface and the **`Dispose`** method pattern.
- **Considerations**: Finalizers delay the object's memory being reclaimed and can lead to performance overhead. They run on a separate, single-threaded finalizer thread, which can cause contention and delays in a heavily loaded system.

### **How the GC Works**

    The .NET Garbage Collector operates on the principle of managed memory, automatically managing the allocation and release of memory for managed objects. It works by:

    1. **Marking**: Identifying which objects are still in use by traversing the object graph from root references.
    2. **Compacting**: Reclaiming the memory occupied by unreachable objects and compacting the remaining objects to reduce fragmentation.
    3. **Generation**: Objects are categorized into generations (0, 1, and 2) based on their lifetime, with newly created objects in generation 0. The GC collects younger generations more frequently, as short-lived objects are more common and less costly to collect.

### **Managed Memory Leaks**

    Despite automatic memory management, it's still possible to encounter "memory leaks" in managed code, typically due to objects that remain reachable and thus are not collected by the GC. Common causes include:

- **Static References**: Objects referenced by static fields are alive for the application's lifetime unless explicitly set to null.
- **Event Handlers**: Not unregistering event handlers can keep objects alive longer than intended.
- **IDisposable Pattern**: Not properly disposing of objects that implement **`IDisposable`** can keep associated unmanaged resources allocated.

### **Best Practices for Memory Management**

- **Dispose Pattern**: Implement the **`IDisposable`** interface and the dispose pattern for classes that use unmanaged resources. Always call **`Dispose`** on IDisposable objects once you're done with them, preferably with a **`using`** statement.
- **Finalizers**: Avoid finalizers unless necessary. Prefer the **`IDisposable`** pattern for cleaning up unmanaged resources.
- **Event Handlers**: Ensure that you unsubscribe from events when the subscriber needs to be collected.
- **Monitor Memory Usage**: Use diagnostic tools (like Visual Studio diagnostics tools, dotMemory) to monitor your application's memory usage and to identify potential memory leaks.
