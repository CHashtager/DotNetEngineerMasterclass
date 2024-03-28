# Indexing

Creating a data structure (an index) that allows for faster searches. Indexes are created on columns that are used frequently in query predicates (e.g., WHERE clauses, JOIN conditions). When an index is created, the DBMS maintains a separate data structure (usually a B-tree or a hash table) that maps the values of the indexed column(s) to the corresponding row locations in the table.

- Indexes improve query performance by providing faster data access
- Trade-off between read and write performance
  - This is because the index must be updated whenever data in the indexed column is added, removed, or altered, which can slow down these operations.
- Indexes consume additional desk spaces causes Storage Overhead
- Maintenance Cost

## **Choosing Columns to Index**

The decision to create an index on a particular column or set of columns should be informed by the specific queries that are most important for the application's performance. Key considerations include:

- Columns used frequently in WHERE clauses.
- Columns used in JOIN conditions.
- Columns used for sorting data (ORDER BY).

## **Clustered Index**

- **Definition**: A clustered index determines the physical order of data in a table. It sorts and stores the data rows in the table based on the indexed columns. Because of this, each table can have only one clustered index.
- **Key Characteristics**:
  - The leaf nodes of a clustered index contain the actual data rows of the table.
  - Searching for data using the clustered index is fast because the index search can lead directly to the data row.
  - Clustered indexes are particularly efficient for range queries that retrieve a range of values.
- **Considerations**:
  - Since the clustered index defines the physical order of data, inserting and updating operations can be slower, especially if the new data must be inserted in the middle of existing data, potentially causing page splits.
  - The choice of the clustered index is critical because it affects the overall storage and access patterns of the data.

## **Non-Clustered Index**

- **Definition**: A non-clustered index is a type of index where the order of the index keys (columns) is separate from the physical order of the rows in the table. A table can have multiple non-clustered indexes.
- **Key Characteristics**:
  - The leaf nodes of a non-clustered index contain index keys and pointers to the corresponding data rows. These pointers are either the clustered index key (if one exists) or a row identifier (RID) if the table is a heap (without a clustered index).
  - Non-clustered indexes are beneficial for quickly accessing data based on the indexed column(s), without affecting the physical order of the table.
  - They are ideal for columns used frequently in search conditions (**`WHERE`** clauses) or join conditions but not as the primary means of accessing data.
- **Considerations**:
  - Non-clustered indexes consume additional disk space because they are stored separately from the table data.
  - Care must be taken not to create too many non-clustered indexes on a table, as this can degrade write performance due to the overhead of maintaining multiple indexes during data modification operations.
