# Concepts

## Normalization

The main goals of normalization include reducing redundancy, organizing data efficiently, and ensuring data integrity.

- Suitable for Online Transaction Processing (OLTP) systems
  - Efficiency and speed of transactions are critical
- **1NF (First Normal Form):** Eliminate duplicate columns from the same table, each piece of data in the table is stored in its smallest possible form.
- **2NF (Second Normal Form):** Non-prime attributes are fully dependent on the primary key
- **3NF (Third Normal Form):** No transitive dependencies, ensuring data integrity

## Denormalization

Denormalization is a strategy used in database design to improve the read performance of a database at the cost of some redundancy and potential loss in data integrity.

- Suitable for Online Analytical Processing (OLAP) systems
  - complex queries and analyses over large volumes of data
  - require fast query performance to handle aggregations, summaries, and analyses across vast datasets
  - The emphasis is on optimizing the speed and efficiency of complex queries rather than on transactional integrity.
- Improves query performance by adding redundant data
- Trades off data integrity for read efficiency

## **When to Use Denormalization**

- The database is read-heavy, and there is a clear need for optimizing query performance over transactional updates.
- Data is relatively static, and updates are infrequent, minimizing the risks and overheads associated with maintaining redundant data.
- The complexity of queries and the size of the datasets involved justify the trade-offs in terms of data redundancy and integrity.
