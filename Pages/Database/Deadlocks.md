# Deadlocks

- Occur when two or more transactions are waiting for one another to release resources
- **SQL Server Deadlock Resolution:**
  - Chooses to terminate the transaction that did the least work (based on transaction log)
  - **DEADLOCK_PRIORITY:** Sets priority for which transaction is chosen
- **Deadly Embrace Deadlock:** Circular chain of two or more threads, with each holding one or more resources that are being requested by another thread
