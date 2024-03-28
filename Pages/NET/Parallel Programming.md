# Parallel Programming

- Writing parallel and concurrent code in C#.

## **Channel**

- **Overview:** Channels are used for producer-consumer scenarios, where one or more tasks are producing data and one or more tasks are consuming that data. They are part of the **`System.Threading.Channels`** namespace introduced in .NET Core 3.0.
- **Usage:** Channels are useful for coordinating between async operations, allowing for efficient and safe passing of data between threads or tasks.

## **Data Parallelism and Task Parallelism**

- **Data Parallelism:** Involves breaking down a data set into smaller chunks and processing each chunk in parallel. This is particularly effective for operations that can be performed independently on segments of data.
- **Task Parallelism:** Refers to executing different tasks in parallel, where each task can perform a different operation. It’s useful when different operations can be performed concurrently.

## **PLINQ (Parallel LINQ)**

- **Overview:** PLINQ extends LINQ to allow query operations to run in parallel, automatically splitting the data source across multiple threads and combining the results once all threads complete.
- **Usage:** Best suited for CPU-intensive query operations over large data sets. You can convert a LINQ query to PLINQ by calling the **`.AsParallel()`** method on the data source.

## **The Parallel Class**

- **Overview:** The **`System.Threading.Tasks.Parallel`** class provides parallel versions of **`for`** and **`foreach`** loops (**`Parallel.For`** and **`Parallel.ForEach`**), as well as a method for running a set of actions in parallel (**`Parallel.Invoke`**).
- **Usage:** Simplifies parallelizing loops and tasks without manually managing threads or tasks.

## **Task Parallelism**

- **Overview:** In .NET, task parallelism is implemented through the **`Task`** and **`Task<T>`** classes in the **`System.Threading.Tasks`** namespace, allowing for asynchronous and parallel operations.
- **Usage:** You can start new tasks with **`Task.Run()`** or create tasks for parallel operations using **`Task.WhenAll()`** or **`Task.WhenAny()`** for coordinating multiple tasks.

## **Concurrent Collections**

- **Overview:** The **`System.Collections.Concurrent`** namespace provides thread-safe collection classes like **`ConcurrentBag<T>`**, **`ConcurrentQueue<T>`**, **`ConcurrentStack<T>`**, and **`ConcurrentDictionary<TKey,TValue>`**.
- **Usage:** These collections are designed for high-performance scenarios where multiple threads are adding, removing, or updating items concurrently.

## **BlockingCollection`<T>`**

- **Overview:** **`BlockingCollection<T>`** is a thread-safe collection class that provides blocking and bounding capabilities for both producer and consumer scenarios.
- **Usage:** It is particularly useful in scenarios where producers may produce data at a faster rate than consumers can consume it, or vice versa, as it can limit the size of the collection and block adding or taking operations based on the state of the collection.
