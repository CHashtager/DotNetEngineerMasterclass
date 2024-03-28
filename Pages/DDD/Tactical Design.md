# Tactical Design

## Aggregate Root & Aggregate

Defining the root entity that controls access to a cluster of related entities.

- **Purpose:** An Aggregate is a cluster of domain objects that can be treated as a single unit for data changes. The Aggregate Root is the main entity within the Aggregate, through which all interactions with the Aggregate's entities should occur. This concept helps in enforcing business rules and ensuring consistency.
- **Application:** Use an Aggregate Root to control access and changes to data within the Aggregate, ensuring integrity and consistency according to the domain rules.

## Value-Object

Objects without an identity, defined by their attributes.

- **Purpose:** Value Objects are objects that are defined entirely by their attributes and do not have a distinct identity. They are often used to represent concepts within the domain that are important for the definition but do not require identity tracking.
- **Application:** Implement common domain concepts like Money, Quantity, or Address as Value Objects to enhance readability and ensure domain logic consistency.

## Domain Services

Services that encapsulate domain logic not fitting naturally into entities or value objects.

- **Purpose:** Domain Services encapsulate business logic that doesn't naturally fit within the context of an entity or value object. These services are stateless and usually operate on domain objects.
- **Application:** Use Domain Services for operations that span multiple aggregates or when an action does not belong to a single entity or value object.

## Application Services

Orchestrating the execution of application use cases.

- **Purpose:** Application Services act as the interface between the outside world and the domain model. They orchestrate the execution of domain operations and transactions, coordinating the flow of data in and out of the domain model.
- **Application:** Implement use cases or business processes by coordinating calls to methods on entities and domain services, managing transaction boundaries and security.

## Domain Events

Events representing state changes within the domain.

- **Purpose:** Domain Events are significant events within the domain model that represent state changes or important occurrences. They facilitate communication between parts of the system in a decoupled manner.
- **Application:** Use Domain Events to notify other parts of the system about changes or important occurrences, enabling reactions to these events without tight coupling.

## Context Mapping

Strategies for dealing with the interconnection of different bounded contexts.

- **Purpose:** Context Mapping identifies and documents the relationships and interactions between different bounded contexts in a system. It helps in understanding and managing dependencies and integrations.
- **Application:** Use Context Mapping to document and design the integration points between bounded contexts, choosing appropriate patterns and strategies for each interaction.

## Integration between BCs (Messaging, RPC, ...)

Mechanisms for communication and integration between bounded contexts.

- **Purpose:** Defines the mechanisms for bounded contexts to communicate and integrate with each other, ensuring data consistency and integrity across the system.
- **Application:** Implement communication between bounded contexts using messaging for asynchronous integration or RPC for synchronous calls, based on the needs of the application.

## Entity Persistence

Storing and retrieving domain entities from a data store.

- **Purpose:** Concerned with how entities and aggregates are stored and retrieved from a persistent storage mechanism, like a database.
- **Application:** Design persistence mechanisms that translate between the database schema and the domain model, ensuring that domain logic remains isolated from data access concerns.
