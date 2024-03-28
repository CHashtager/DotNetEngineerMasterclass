# CAP Theorem

- **Consistency**
  - Consistency means that all nodes see the same data at the same time. Precisely, any read operation on the system returns the value of the most recent write operation. Consistency ensures that a system behaves much like a single, non-distributed system, from the perspective of its users.
- **Availability**
  - Availability ensures that every request receives a response, regardless of the success or failure of the operation. In practical terms, it means that every request made to the system must result in some kind of response to the client, even if a network partition occurs.
- **Partition Tolerance**
  - Partition Tolerance means that the system continues to operate despite arbitrary message loss or failure of part of the system (i.e., network partitions). A partition-tolerant system can sustain any amount of network failure that does not result in a failure of the entire network.
- Describes the trade-offs between Consistency, Availability, and Partition Tolerance
  - **CP (Consistency and Partition Tolerance):** The system prioritizes consistency and partition tolerance over availability. This means that in the event of a network partition, the system might choose to respond only to requests that can be served with consistent data, potentially sacrificing availability for some nodes.
  - **AP (Availability and Partition Tolerance):** The system prioritizes availability and partition tolerance over consistency. In the case of a network partition, the system will continue to operate and respond to requests, even if it cannot guarantee that all nodes have the most recent data. Eventually consistent systems, which allow for temporary inconsistencies but converge towards consistency over time, often fall into this category.
  - **CA (Consistency and Availability):** While theoretically a system could choose to prioritize consistency and availability, in practice, this choice is not viable for distributed systems because partition tolerance is a necessity in any networked environment. Thus, CA systems are typically not considered in the context of the CAP Theorem, which focuses on distributed systems where network partitions are a given.
- In the presence of network partitions, a distributed system must choose between CP or AP
