# Basics

## **Concurrency vs Multi-Threading vs Async vs Parallelism**

- **Concurrency** is about dealing with lots of things at once, like managing multiple tasks within an application.
- **Multi-Threading** involves executing multiple threads simultaneously, allowing for parallel execution of code.
- **Async** programming is about performing tasks without blocking the execution thread, improving responsiveness.
- **Parallelism** is the simultaneous execution of (possibly related) computations across multiple processors or cores.

---

- **Concurrency:** Multiple tasks making progress, not necessarily simultaneously.
- **Multi-Threading:** Multiple threads executing code simultaneously.
- **Async:** Asynchronous programming, allowing non-blocking execution.
- **Parallelism:** Simultaneous execution of tasks on multiple processors.

## Single-core vs Multicore/Multiprocessor Machine

- On a **single-core** machine, multi-threading and async programming can improve responsiveness but don't increase execution speed.
- **Multicore/multiprocessor** machines can run threads in parallel, truly speeding up execution.

## Related Data-Structures

- **Concurrent Collections** like **`ConcurrentDictionary`**, **`BlockingCollection`**, and channels in **`System.Threading.Channels`** enable safe and efficient management of data in multithreaded scenarios.

## ConcurrentDictionary

- A thread-safe dictionary that allows concurrent read and write operations.

## ConcurrentQueue

- A thread-safe queue for concurrent producer and consumer scenarios.

## Channels

- A more advanced concurrency primitive for communication between producers and consumers.
