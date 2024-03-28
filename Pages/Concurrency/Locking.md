# Locking

Prevent multiple threads from modifying shared resources simultaneously, which can lead to data corruption and unpredictable behavior.

- Ways
  - `lock` keyword
    - **Usage**: The **`lock`** keyword is a simple and convenient way to synchronize access to blocks of code to ensure that only one thread can execute them at a time. It's primarily used for locking small sections of code for short durations.
    - **Internally**: Under the hood, the **`lock`** keyword uses the **`Monitor`** class to acquire an exclusive lock on an object. If another thread has already acquired the lock, the current thread will block until the lock becomes available.
    - **Example**:

            ```csharp
            private readonly object _lockObject = new object();
            
            public void CriticalSection()
            {
                lock (_lockObject)
                {
                    // Thread-safe code here
                }
            }
            ```

  - **`Monitor.Enter` / `Monitor.Exit`**
    - **Usage**: Provides functionality similar to the **`lock`** keyword but with more control over the locking mechanism. It's useful when more flexibility is needed, such as attempting to acquire a lock without blocking indefinitely.
    - **Internally**: Directly manages the acquisition and release of locks on objects. You must ensure **`Monitor.Exit`** is called to release the lock, typically within a **`finally`** block to guarantee execution.
    - **Example**:

            ```csharp
            private readonly object _lockObject = new object();
            
            public void CriticalSection()
            {
                bool lockTaken = false;
                try
                {
                    Monitor.Enter(_lockObject, ref lockTaken);
                    // Thread-safe code here
                }
                finally
                {
                    if (lockTaken)
                    {
                        Monitor.Exit(_lockObject);
                    }
                }
            }
            ```

  - Semaphore
    - **Usage:** Limits the number of threads that can access a resource concurrently. A semaphore maintains a count of permits, and threads must acquire a permit to proceed, which they release when they're done.
    - **Internally**: Manages a counter to keep track of the number of available permits. Threads wait if no permits are available and proceed when they can acquire a permit.
    - **Example:**

            ```csharp
            private static Semaphore _semaphore = new Semaphore(3, 3); // Maximum of 3 concurrent threads
            
            public void AccessResource()
            {
                _semaphore.WaitOne(); // Acquire a permit
                try
                {
                    // Access the shared resource
                }
                finally
                {
                    _semaphore.Release(); // Release the permit
                }
            }
            ```

  - Semaphore-Slim
    - **Usage:** A lightweight alternative to Semaphore for limiting concurrent access.
    - **Internally:** Uses efficient signaling mechanisms.
    - **Example:**

            ```csharp
            private static SemaphoreSlim _semaphoreSlim = new SemaphoreSlim(3, 3);
            
            public async Task AccessResourceAsync()
            {
                await _semaphoreSlim.WaitAsync(); // Asynchronously wait to acquire the semaphore
                try
                {
                    // Access the shared resource
                }
                finally
                {
                    _semaphoreSlim.Release();
                }
            }
            ```
