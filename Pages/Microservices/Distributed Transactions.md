# Distributed Transactions

- Maintaining data consistency across multiple services and databases is a challenge.
- Patterns like Saga, Event Sourcing, and Outbox can be employed to ensure eventual consistency.
- two-phase commit
  - A classic distributed transaction protocol involving two phases to ensure atomicity.
- **Saga Pattern**
  - **Overview:** A Saga is a sequence of local transactions where each transaction updates data within a single service and publishes an event or message to trigger the next transaction in another service. Sagas can be orchestrated, where a central coordinator manages the sequence of transactions, or choreographed, with each service producing and consuming events independently.
  - **Consistency:** Sagas ensure eventual consistency by compensating for previous transactions in the case of a failure. If one transaction fails, compensating transactions are executed to undo the impact of the preceding transactions in the sequence.
  - **Use Cases:** Suitable for long-running business processes and workflows where different steps need to be executed by different microservices.
- **Event Sourcing**
  - **Overview:** Event Sourcing persists the state of an entity as a sequence of state-changing events. Instead of storing just the current state of data, every change is captured in an event with enough information to reconstruct past states.
  - **Consistency:** Ensures consistency by applying events in a sequence, which can be replayed to reach the current state. It naturally aligns with the CQRS (Command Query Responsibility Segregation) pattern, allowing for separate models for reads and writes.
  - **Use Cases:** Useful for systems that require a detailed audit log, complex business processes, or those that benefit from analyzing past actions.
- **Outbox Pattern**
  - **Overview:** The Outbox pattern involves storing events or messages in a local outbox (a database table or similar storage) as part of the local transaction. A separate process or worker then retrieves these messages from the outbox and publishes them to the message broker or event bus, ensuring that the local transaction and the publishing of the event are not directly coupled.
  - **Consistency:** Helps achieve eventual consistency by ensuring that messages are not lost even if the message broker is temporarily unavailable. Messages are guaranteed to be published once the local transaction succeeds.
  - **Use Cases:** Effective in scenarios where reliability and consistency of event publishing are critical, especially in distributed systems with network latency or intermittent connectivity issues.
