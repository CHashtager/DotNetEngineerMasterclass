# Threading

- **Sleep, Yield, Blocking, and Spinning** are mechanisms to manage thread execution and synchronization.
- **Foreground vs Background Threads:** Foreground threads keep an application running, while background threads don't prevent an application from terminating.
- **The Thread Pool** optimizes and manages a pool of threads for short-lived operations.
- **Tasks and `Task.Run()`** are used for asynchronous operations, offering a higher-level abstraction over threads.
- **Exception Handling** in asynchronous code involves capturing exceptions in tasks and using **`try-catch`** blocks.
- **`async void`** methods are generally discouraged except for event handlers due to exception handling complexities.
- **`ConfigureAwait(false)`** can be used in library code to avoid deadlocks by not capturing the synchronization context.
- **Cancellation** involves using **`CancellationToken`** and **`CancellationTokenSource`** to cancel asynchronous operations gracefully.
- **Synchronization** objects like **`SemaphoreSlim`**, **`Mutex`**, and **`ReaderWriterLockSlim`** help manage access to shared resources.
