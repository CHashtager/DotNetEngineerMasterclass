# Cancellation Token

- **Usages:** Cancels asynchronous operations.
- Managing cancellation in asynchronous and long-running operations.
- These mechanisms allow developers to cooperatively cancel tasks or operations when needed, such as when the user requests cancellation, an operation times out, or when shutting down an application gracefully.

## **Creating a CancellationToken Using CancellationTokenSource**

A **`CancellationToken`** cannot be instantiated directly; instead, it is created through a **`CancellationTokenSource`** (CTS). The CTS provides the capability to signal cancellation to one or more tokens.

```csharp
var cancellationTokenSource = new CancellationTokenSource();
var cancellationToken = cancellationTokenSource.Token;
```

## **Canceling a CPU-Bound Task**

You can pass a **`CancellationToken`** to any task or operation that supports cancellation. It's up to the operation to check the cancellation token periodically and stop its work if cancellation has been requested.

```csharp
Task.Run(() =>
{
    for (int i = 0; i < 100; i++)
    {
        if (cancellationToken.IsCancellationRequested)
        {
            Console.WriteLine("Cancellation requested.");
            break; // Exit the loop to cancel the operation
        }

        // Simulate work
        Thread.Sleep(100);
    }
}, cancellationToken);
```

To request cancellation from another part of the application, you call **`Cancel`** on the **`CancellationTokenSource`**:

```csharp
cancellationTokenSource.Cancel();
```

## **Timeout an Async Task Using CancellationTokens**

To implement a timeout for an asynchronous operation, you can use the **`CancellationTokenSource`** constructor that takes a timespan or milliseconds as an argument. This automatically cancels the token after the specified duration.

```csharp
var timeout = TimeSpan.FromSeconds(30);
var cancellationTokenSource = new CancellationTokenSource(timeout);
var cancellationToken = cancellationTokenSource.Token;

try
{
    await Task.Run(async () =>
    {
        // Long-running operation
        await Task.Delay(TimeSpan.FromMinutes(1), cancellationToken);
    }, cancellationToken);
}
catch (TaskCanceledException)
{
    Console.WriteLine("The operation has been canceled due to a timeout.");
}
```

In this example, if the task does not complete within 30 seconds, the **`CancellationToken`** is cancelled, which in turn throws a **`TaskCanceledException`**. This allows the operation to be stopped due to the timeout.

## **Best Practices**

- **Cooperative Cancellation**: Cancellation in .NET is cooperative, meaning the operation being canceled must periodically check the **`CancellationToken`** and respond to cancellation requests.
- **Handle TaskCanceledException**: When awaiting a task that receives a **`CancellationToken`**, be prepared to handle **`TaskCanceledException`** to manage task cancellation gracefully.
- **Dispose of CancellationTokenSource**: It's good practice to dispose of **`CancellationTokenSource`** instances using **`using`** statements or manually calling **`Dispose()`** to free up resources.
