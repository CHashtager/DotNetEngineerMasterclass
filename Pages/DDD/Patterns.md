# Patterns

## Factory

Creating objects without specifying the exact class.

- **Purpose:** Factories encapsulate the logic of creating instances of complex objects or aggregates, ensuring that all necessary initializations are performed.
- **Application:** Use factories when creating an object involves more than just instantiating a class, especially when dealing with complex aggregates.

## Repository

Mediating between the domain and data mapping layers.

- **Purpose:** Repositories abstract the mechanism of storing and retrieving domain entities, providing a collection-like interface for accessing domain objects.
- **Application:** Implement repositories for each Aggregate Root to encapsulate all code needed to retrieve and persist those aggregates.

## Unit of Work

Maintaining a list of objects affected by a business transaction.

- **Purpose:** Maintains knowledge of all changes to objects (entities or aggregates) within a business transaction and coordinates the writing out of changes and the resolution of concurrency problems.
- **Application:** Use in scenarios where multiple changes to the domain model need to be coordinated and persisted atomically.

## Event Sourcing

Storing the state of an entity as a sequence of events.

- **Purpose:** Instead of storing just the current state of an entity, Event Sourcing stores each state-changing operation as a unique event. The current state can be reconstructed by replaying these events.
- **Application:** Useful for systems where understanding the sequence of events leading to a state is crucial, such as in auditing or complex business processes.

## CQRS

Separating read and write operations for data storage.

- **Purpose:** Separates the models for reading data from the models for updating data, allowing optimizations for each function and improving scalability and performance.
- **Application:** Implement in systems where the read and write workloads are significantly different or where a clear separation can simplify the design and improve performance.
