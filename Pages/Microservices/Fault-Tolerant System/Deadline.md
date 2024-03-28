# Deadline

Deadlines extend the concept of timeouts by setting a fixed point in time by which an operation or a series of operations must complete. Unlike timeouts, which are typically set for individual operations and measure the duration of those operations, deadlines are absolute and can encompass multiple steps or stages in a process.

- Deadlines set a maximum time limit for completing an operation, preventing requests from getting stuck indefinitely.
- After the deadline, the operation can be canceled, retried, or a fallback can be used.
- **Application:** Deadlines are particularly useful in scenarios involving multiple sequential or parallel operations that together accomplish a task. For instance, in a microservices architecture, a request might involve calls to several services; a deadline ensures the entire process completes within a specific timeframe.
- **Behavior After Deadline:** Similar to timeouts, when a deadline is reached, the system can:
  - **Cancel or abort the ongoing operation**, freeing up resources and potentially notifying the user or system that initiated the request.
  - **Retry parts of the process** if there's a policy in place for handling partial completions or if specific operations are identified as having caused the delay.
  - **Use a fallback mechanism** to provide a degraded but immediate response to the request.
