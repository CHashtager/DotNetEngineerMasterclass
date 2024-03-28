# Transactions and Isolation Levels

- **ACID vs. BASE:** ACID for strong consistency, BASE for eventual consistency
  - **ACID (Atomicity, Consistency, Isolation, Durability)**: This model focuses on strong consistency and reliability of transactions. Each transaction is treated as a single unit, which either completely succeeds or fails, leaving the database in a consistent state. ACID-compliant systems prioritize correctness and consistency, making them ideal for scenarios where data integrity is paramount.
    - **Atomicity**: Ensures that each transaction is treated as a single unit, which either fully happens or does not happen at all.
    - **Consistency**: Ensures that a transaction can only bring the database from one valid state to another, maintaining the integrity of the database.
    - **Isolation**: Ensures that concurrent transactions do not affect each other’s execution.
    - **Durability**: Ensures that once a transaction has been committed, it will remain so, even in the event of power loss, crashes, or errors.
  - **BASE (Basically Available, Soft state, Eventually consistent)**: This model is designed for distributed systems and prioritizes availability over immediate consistency. BASE-compliant systems are more flexible and scalable, offering eventual consistency. They are well-suited for environments where absolute consistency can be momentarily sacrificed for higher availability and partition tolerance.
    - **Basically Available**: Indicates that the system guarantees availability.
    - **Soft state**: The state of the system may change over time, even without input.
    - **Eventually consistent**: The system will become consistent over time, given that the system does not receive input during that time.
- **Isolation Levels:**

**Dirty reads:** transactions can read data that has not yet been committed by other transactions

- **READ UNCOMMITTED:** Allows dirty reads, lowest isolation level
  - This level can lead to inconsistencies and is generally not used if data integrity is a concern.
- **READ COMMITTED:** Prevents dirty reads, but allows non-repeatable reads
  - a transaction may read the same row multiple times and see different data, which has been modified by other transactions between reads.
- **REPEATABLE READ:** Prevents non-repeatable reads, but allows phantom reads
  - This level does not prevent phantom reads, where new rows added to the dataset by another transaction might appear in subsequent reads within the same transaction.
- **SERIALIZABLE:** Highest isolation level, prevents phantom reads
  - This level ensures full ACID compliance but can lead to decreased performance and increased locking overhead.

## Row Versioning Isolation Levels

Designed to enhance concurrency while minimizing issues like locks and blocking, which can occur in traditional locking mechanisms.

- **SNAPSHOT:** Uses row versioning to provide a consistent view of data
  - Throughout the transaction's execution, it sees a stable snapshot of the data as it was at the start of the transaction, regardless of subsequent changes made by other transactions. This isolation level uses row versioning to maintain historical versions of rows. When a transaction reads data, it sees the version of the rows that existed when the transaction started, ensuring that the data remains consistent throughout the transaction's execution.
  - Benefits:
    - Elimination of locking and blocking problems, enhancing system concurrency.
    - Prevention of dirty reads, non-repeatable reads, and phantom reads within the scope of the transaction.
  - Not suitable for those requiring real-time data accuracy, because a transaction will not see changes made by other transactions after it has started.
- **READ COMMITTED SNAPSHOT (RCS):** Combines read committed and row versioning
  - Each query in a transaction sees a consistent snapshot of the database as it was at the beginning of the query, rather than at the beginning of the transaction. This means that if a transaction issues multiple queries, each query can see changes committed by other transactions between the individual queries within the same transaction.
  - Benefits:
    - It prevents dirty reads by ensuring that a query only sees data that has been committed before the query started.
    - It allows for higher concurrency than traditional READ COMMITTED isolation because it reduces locking by using row versioning instead.
  - Unlike the SNAPSHOT isolation level, RCS does not prevent non-repeatable reads or phantom reads between separate queries within the same transaction, because each query can see a newer state of the database.
