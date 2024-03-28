# Async & Task Internals

- **At least, how many threads are needed to run an async task?**
  - Async tasks can execute on a single thread.
    - The number of threads required to run an async task can actually be as few as zero for the task's execution itself. This is because async tasks in C# are not inherently about creating new threads. Instead, they are about performing non-blocking operations, allowing the current thread to continue executing other work while the asynchronous operation is pending.
        1. **Async operations without explicit threading**: When you await an async operation (e.g., I/O operations like reading a file or querying a database), the operation is performed without blocking the calling thread. The magic here is that the operation can leverage I/O completion ports or other non-thread-based asynchronous mechanisms provided by the underlying OS or framework. For these types of operations, no additional threads are needed. Once the operation completes, the continuation (the code after the **`await`** in your method) is scheduled to run on a synchronization context, which might not necessarily be a new thread.
        2. **Synchronization Context**: The synchronization context controls how the continuations are executed after an async operation completes. In a GUI application (like Windows Forms or WPF), the synchronization context ensures that the continuation runs on the UI thread, thus allowing the UI to be updated safely. In server-side applications (like ASP.NET), the synchronization context might utilize a thread pool to efficiently manage a large number of concurrent operations without creating new threads for each.
        3. **Thread Pool**: While not strictly required for running an async task, the .NET thread pool is often involved in the execution of task continuations, especially in the absence of a SynchronizationContext or when explicitly requested. The thread pool efficiently manages a collection of threads that can be used to execute task continuations, avoiding the overhead of creating new threads for short-lived operations.
    - **you do not necessarily need any additional threads to run an async task** in C#. The task can be executed asynchronously on the same thread, leveraging the underlying asynchronous mechanisms of the OS or framework, especially for I/O-bound operations.
- **`GetAwaiter().GetResult()` vs `.Result`**
  - Both block the calling thread until the task completes.
  - **`.Result`**: Encapsulates any exceptions thrown by the task into an **`AggregateException`**, which can make error handling cumbersome.
  - **`GetAwaiter().GetResult()`**: Throws the original exception without wrapping it in an **`AggregateException`**, making it more straightforward for exception handling.
- **`Task` vs `ValueTask`**
  - `Task` represents a potentially asynchronous operation.
  - `ValueTask` is a more lightweight option for small, synchronous tasks.
- **`Task.WhenAll` & `Task.WhenAny`**
  - `WhenAll` waits for all tasks to complete.
    - It's useful for running parallel operations that are independent of each other.
  - `WhenAny` waits for any of the tasks to complete.
    - This can be used to implement timeouts or to process tasks as they complete.
- **`FooAsync.Wait()` & `FooAsync.WaitAsync()`**
  - `Wait` blocks the calling thread till the async operation completes.
    - It's prone to causing deadlocks, especially in UI applications or [ASP.NET](http://asp.net/) contexts, and is generally discouraged.
  - `WaitAsync` is an asynchronous wait, allowing non-blocking usage.
- **Why is `async void` bad? When do we have to use it?**
  - Async void is not awaitable and can't be caught in exceptions.
  - Used in event handlers and other scenarios where async void is required.

## **Best Practices**

- Avoid blocking calls (**`Result`**, **`.Wait()`**, **`GetAwaiter().GetResult()`**) in asynchronous code to prevent deadlocks.
- Prefer **`async Task`** over **`async void`** for asynchronous methods to allow proper exception handling and awaitability.
- Use **`ValueTask`** in performance-critical paths where operations may complete synchronously.
- Leverage **`Task.WhenAll`** and **`Task.WhenAny`** to coordinate multiple asynchronous operations effectively.

## `Task.Run`

- Queues the specified work to run on the `ThreadPool`.
- **Functionality**: **`Task.Run`** takes an **`Action`** or **`Func<T>`** delegate, queues it to run on the `ThreadPool`, and returns a **`Task`** or **`Task<T>`** that represents the asynchronous operation.
- **Usage Scenario**: It's particularly useful for performing CPU-bound work asynchronously or when you need to run a long-running operation without blocking the calling thread.
- **`ThreadPool` Utilization**: **`Task.Run`** does not inherently create a new thread. Instead, it schedules the work to be run on an existing thread in the `ThreadPool`. The `ThreadPool` manages a pool of worker threads for the application, dynamically adjusting the number of threads as needed.
- **Efficiency**: This is more efficient than creating new threads for each task because thread creation and destruction are costly operations. The `ThreadPool` helps reduce this overhead by reusing threads.

## `Thread.Sleep` vs `Task.Delay`

- **`Thread.Sleep`:** Blocks the current thread.
  - **What it does**: **`Thread.Sleep`** pauses the current thread for a specified amount of time. During this time, the thread is blocked and does not consume CPU cycles. However, it prevents the thread from doing any work or processing any I/O operations.
  - **Usage scenario**: It's used in synchronous programming models, especially when a delay is required in background processing or non-UI threads. However, its use is generally discouraged in modern application development, particularly on the UI thread, as it can make the application unresponsive.
- **`Task.Delay`:** Delays without blocking the thread, suitable for asynchronous scenarios.
  - **What it does**: **`Task.Delay`** creates a task that completes after a specified time period. It does not block the thread on which it is called; instead, it uses timers to complete the task after the delay. This allows the awaiting thread to be freed up to perform other work.
  - **Usage scenario**: Ideal for asynchronous programming patterns. It's often used in UI applications to prevent freezing the UI thread, and in server applications to implement non-blocking delays.

## **Key Differences**

- **Blocking vs. Non-Blocking**: **`Thread.Sleep`** blocks the thread, making it inactive. **`Task.Delay`** does not block the thread, allowing other operations to be processed.
- **Use in Async Methods**: **`Task.Delay`** can be awaited in asynchronous methods, making it suitable for async programming patterns. **`Thread.Sleep`** has no place in async methods as it causes blocking, which is counterproductive to the goals of asynchronous execution.

## Long-running threads (`ThreadPool` effects, Implementation via `TaskFactory`)

- Long-running tasks may tie up `ThreadPool` threads.
  - Long-running tasks can tie up `ThreadPool` threads, leading to a situation where there are not enough threads available to process other tasks or requests. This can result in delays in processing or a complete stall in application responsiveness, especially under heavy loads or when many long-running tasks are initiated.
- `TaskFactory` can be used to create long-running tasks.
  - To mitigate the impact of long-running tasks on the `ThreadPool`, .NET provides a way to explicitly indicate that a task is expected to be long-running. This can be done using the **`TaskFactory.StartNew`** method with the **`TaskCreationOptions.LongRunning`** option. This hint allows the Task Parallel Library (TPL) to manage the task more appropriately, often by starting a new dedicated thread rather than borrowing a thread from the `ThreadPool`.

## **Considerations**

- **Use Sparingly**: The creation of too many dedicated threads can lead to resource contention and diminish the benefits of using the `ThreadPool`. The **`LongRunning`** option should be used judiciously, only for tasks that are truly long-running and cannot be efficiently broken down into smaller, shorter-running tasks.
- **Alternative Approaches**: For I/O-bound operations that are long-running due to waiting on I/O resources (e.g., network responses, file I/O), consider using asynchronous I/O operations (**`await`** on asynchronous methods like **`ReadAsync`**, **`WriteAsync`**, etc.) instead of dedicating a thread to wait. This approach frees up the thread to process other work while waiting for the I/O operation to complete.
- **`ThreadPool` Starvation**: Be aware of `ThreadPool` starvation, which occurs when all `ThreadPool` threads are busy or blocked, causing new work items to wait for an available thread. Proper task management and avoiding unnecessary long-running tasks can help prevent this issue.
