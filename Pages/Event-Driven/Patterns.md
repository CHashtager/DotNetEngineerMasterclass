# Patterns

- **Event Sourcing:**
  - Involves storing changes to the application state as a sequence of events
  - Events are persisted as an immutable sequence, enabling reconstruction of application state.
  - Updates are atomic, with events published after successful state changes.
  - Outbox Pattern provides reliable event publishing, while Event Sourcing focuses on state management.
- **Outbox Pattern:**
  - Ensures reliable event publishing by storing events in an outbox table before publishing.
  - Provides transactional consistency between data changes and event publishing.
  - Change Data Capture (CDC) is a technique for capturing and publishing data changes as events.
- **CQRS (Command Query Responsibility Segregation):**
  - Separates read and write operations into different models and data stores.
  - Queries can be implemented by fetching data from multiple services and combining the results. **(Flexibility in Query Implementation)**
