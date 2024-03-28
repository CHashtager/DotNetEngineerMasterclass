# Strategies

## Optimistic

- **Approach:** Assumes that conflicts between threads are infrequent.
- **Locking:** Limited use of locks, optimistic about minimal contention.

## Pessimistic

- **Approach:** Assumes that conflicts between threads are frequent and takes precautions.
- **Locking:** More liberal use of locks to avoid potential contention.

## **Optimistic Concurrency Control**

- **Approach**: Optimistic concurrency control operates under the assumption that conflicts for resources are rare. Instead of locking resources to manage access, it allows multiple transactions or threads to proceed concurrently, checking for conflicts only at the time of committing the changes.
- **Locking Mechanism**: Typically involves little to no use of traditional locks. Instead, it checks if the resource was modified by another transaction or thread since it was last read. This can be implemented using version numbers, timestamps, or checksums. If a conflict is detected (e.g., the resource was modified by another transaction), the current operation may be retried or aborted.
- **Use Cases**: Best suited for environments with low contention and where the cost of rolling back a transaction is less than the cost of locking resources. It's commonly used in web applications and scenarios where read operations significantly outnumber write operations.

## **Pessimistic Concurrency Control**

- **Approach**: Pessimistic concurrency control takes a more cautious approach by assuming that conflicts are likely to occur. To prevent conflicts, it locks resources when they are being read or written to ensure that no other transaction or thread can access the same resource simultaneously.
- **Locking Mechanism**: Involves explicit locking of resources for the duration of a transaction or operation. This can be implemented using database locks (such as row-level locks), mutexes, or semaphores in application code. The locked resources are only released when the transaction is completed or aborted, ensuring exclusive access.
- **Use Cases**: Suitable for environments with high contention or when the integrity of a transaction is critical. It is often used in financial applications, inventory systems, or any scenario where ensuring the success of a transaction outweighs the cost of locking resources.

## **Choosing Between Optimistic and Pessimistic Concurrency Control**

The choice between optimistic and pessimistic concurrency control depends on several factors, including:

- **Contention Level**: Optimistic concurrency is preferred in low-contention scenarios, whereas pessimistic concurrency is suitable for high-contention environments.
- **Operation Type**: Read-heavy workloads might benefit more from optimistic concurrency, while write-heavy or critical operations might require the use of pessimistic concurrency to ensure consistency.
- **Performance and Scalability Requirements**: Optimistic concurrency can offer better performance and scalability in some cases by reducing the overhead associated with locking. However, it might lead to more transaction rollbacks in high-contention scenarios.
- **Application Specifics**: The specific requirements and characteristics of the application, including the cost of transaction rollbacks, the criticality of operations, and user expectations, play a crucial role in determining the appropriate strategy.
