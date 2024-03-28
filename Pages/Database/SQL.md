# SQL

## Constraints

- **Primary Key Constraint:**
  - Enforces uniqueness of rows and disallows NULL values in the constraint attributes
  - SQL Server creates a unique index behind the scenes to enforce the logical primary key constraint
- **Unique Constraint:**
  - SQL Server creates a unique index to enforce the logical unique constraint
  - Two NULL values are considered equal to each other
- **Foreign Key Constraint:** Establishes a relationship between two tables, ensuring referential integrity
- **Check Constraint:** Enforces domain integrity by specifying the valid range of values allowed in a column
- **Default Constraint:** Provides a default value for a column when no value is supplied during INSERT operations

## Inheritance

- **Table-per-Type:** Each concrete type is mapped to a separate table

    The Table-per-Type strategy involves creating a separate table for each type in the inheritance hierarchy, including both the base class and each derived class. Each table contains columns for the properties of that class only. For derived classes, a foreign key is used to associate the derived class table with the base class table, maintaining the inheritance relationship.

    **Advantages:**

  - **Normalization**: The TPT approach adheres to normalization rules, which can reduce redundancy and improve data integrity.
  - **Flexibility**: It's easier to add new classes to the hierarchy, as this typically only requires adding new tables without modifying existing tables.
  - **Query Performance (for specific queries)**: Queries that target a specific type can be more efficient, as they only involve the table corresponding to that type.

    **Disadvantages:**

  - **Complex Queries and Joins**: Retrieving data across the hierarchy can become complex and less performant, as it may require multiple joins between the base table and the derived tables.
  - **Insert and Update Performance**: Operations that affect multiple levels of the hierarchy can be slower due to the need to insert or update records in multiple tables.
- **Table-per-Hierarchy:** All types in the hierarchy are mapped to a single table

    The Table-per-Hierarchy strategy maps the entire class hierarchy to a single table. This table includes columns for all properties of the base class and all derived classes. To differentiate between the types, a discriminator column is used, indicating the specific type each row represents.

    **Advantages:**

  - **Simplicity**: The TPH approach simplifies the database schema by using a single table, making it easier to understand and manage.
  - **Performance**: Operations that affect multiple levels of the hierarchy can be more efficient, as they involve a single table. Queries that need data from multiple types in the hierarchy are also more straightforward and can perform better.

    **Disadvantages:**

  - **Data Redundancy**: The table can contain a lot of null values, especially for columns that are specific to certain derived types but not applicable to others, leading to wasted space.
  - **Schema Changes**: Adding a new class to the hierarchy or changing the properties of a class can require altering the table schema, which can be disruptive.
  - **Less Flexibility in Constraints**: Enforcing constraints that are specific to a derived type can be more challenging, as all data is stored in a single table.

## Subqueries

- **Self-Contained Subquery:**
  - **Scalar Subquery:** Returns a single value
    - Can be used wherever a scalar value is valid, such as in the SELECT list, WHERE clause, or HAVING clause.
    - **Example Usage:** Comparing a column value in the main query to the result of a scalar subquery.

        ```sql
        SELECT employee_name, salary
        FROM employees
        WHERE salary > (SELECT AVG(salary) FROM employees);
        ```

  - **Multivalued Subquery:** Returns a set of values
    - Often used with operators like IN, ANY, or ALL.
    - **Example Usage:** Finding records that match any of the values returned by the subquery.

        ```sql
        SELECT employee_name, department_id
        FROM employees
        WHERE department_id IN (SELECT department_id FROM departments WHERE location_id = 'L001');
        ```

  - **Correlated Subquery:** References columns from the outer query
    - A correlated subquery is a subquery that references columns from the outer query, making it dependent on the outer query. It cannot be executed independently and is evaluated repeatedly for each row processed by the outer query.
    - **Example Usage:** Finding employees whose salary is above the average for their department.

        ```sql
        SELECT e.employee_name, e.salary, e.department_id
        FROM employees e
        WHERE e.salary > (
          SELECT AVG(e2.salary)
          FROM employees e2
          WHERE e2.department_id = e.department_id
        );
        ```

    - Correlated subqueries can be more resource-intensive than self-contained subqueries because the subquery may be executed multiple times, once for each row evaluated by the outer query. Optimizing these queries or rewriting them using JOINs or window functions might improve performance in some databases.

## Table Expressions

- **Derived Table:** A subquery that returns a result set
  - It allows for the encapsulation of complex logic within a subquery, providing a set of results on which the outer query can operate.

    ```sql
    SELECT dt.employee_name, dt.average_salary
    FROM (
        SELECT employee_name, AVG(salary) AS average_salary
        FROM employees
        GROUP BY employee_name
    ) AS dt
    WHERE dt.average_salary > 50000;
    ```

- **View:** A virtual table based on a stored query
  - Can be queried just like a real table.

    ```sql
    CREATE VIEW department_summary AS
    SELECT department_id, COUNT(*) AS employee_count, AVG(salary) AS average_salary
    FROM employees
    GROUP BY department_id;
    
    SELECT * FROM department_summary WHERE average_salary > 60000;
    ```

- **Common Table Expression (CTE):** A temporary named result set derived from a simple query

    ```sql
    WITH ranked_salaries AS (
        SELECT employee_name, salary,
        RANK() OVER (ORDER BY salary DESC) AS rank
        FROM employees
    )
    SELECT employee_name, salary
    FROM ranked_salaries
    WHERE rank <= 5;
    ```

- **Recursive CTE:** Iteratively executes a query until a termination condition is met

    ```sql
    WITH RECURSIVE subordinates AS (
        SELECT employee_id, manager_id, employee_name
        FROM employees
        WHERE employee_id = 1 -- Assuming 1 is the root manager
        UNION ALL
        SELECT e.employee_id, e.manager_id, e.employee_name
        FROM employees e
        INNER JOIN subordinates s ON e.manager_id = s.employee_id
    )
    SELECT * FROM subordinates;
    ```

- **Inline Table-Valued Function:** A user-defined function that returns a table

    ```sql
    CREATE FUNCTION GetEmployeeDetails (@DepartmentId INT)
    RETURNS TABLE
    AS
    RETURN (
        SELECT employee_name, salary
        FROM employees
        WHERE department_id = @DepartmentId
    );
    
    SELECT * FROM GetEmployeeDetails(1); -- Returns details of employees in department 1
    ```

## Operators

- **Cross Apply and Outer Apply:** Used to join tables based on a table expression
- **CROSS APPLY**
  - The **`CROSS APPLY`** operator works like an **`INNER JOIN`** in that it only returns rows from the outer table if the table expression (e.g., a table-valued function or a derived table) returns at least one row. It's a powerful tool for situations where you want to apply a function to each row of a table and only retrieve rows where the function returns a result.
  - **Example Usage:**
    Suppose you have a function **`GetEmployeeProjects`** that returns a list of projects for a given employee ID. You can use **`CROSS APPLY`** to get a list of all employees and their projects:This query returns only those employees who have at least one project.

    ```sql
    SELECT e.employee_name, p.project_name
    FROM employees e
    CROSS APPLY GetEmployeeProjects(e.employee_id) p;
    ```

- **OUTER APPLY**
  - The **`OUTER APPLY`** operator is similar to **`CROSS APPLY`**, but it works more like a **`LEFT JOIN`**. It returns all rows from the outer table, even if the table expression does not return any rows for those outer table rows. When the table expression returns no rows for a given outer row, **`NULL`** values are returned for columns coming from the table expression.
  - **Example Usage:**
    Using the same function **`GetEmployeeProjects`**, you can use **`OUTER APPLY`** to get a list of all employees, including those without projects:This query includes all employees, with **`NULL`** values for **`project_name`** where no projects exist for the employee.

    ```sql
    SELECT e.employee_name, p.project_name
    FROM employees e
    OUTER APPLY GetEmployeeProjects(e.employee_id) p;
    ```

- **Use Cases and Benefits**
  - **Dynamic Table Expressions:** **`APPLY`** allows for complex calculations and transformations that depend on the outer query's rows.
  - **Flexibility:** It offers a flexible way to join rows from a table to a series of rows dynamically generated by a table-valued function or subquery.
  - **Simplifying Queries:** It can simplify queries that would otherwise require complex joins, subqueries, or conditional aggregations.

## Window Functions

- **Ranking Functions:**
- `ROW_NUMBER()`: Assigns a unique sequential number to each row
- `RANK()`: Assigns a rank based on the order of rows, allowing ties
- `DENSE_RANK()`: Assigns a rank based on the order of rows, but without gaps for ties
- `NTILE()`: Distributes rows into a specified number of groups
- **Offset Functions:**
- `LEAD()` and `LAG()`: Access values in rows before or after the current row
- `FIRST_VALUE()` and `LAST_VALUE()`: Access the first or last value in a partition

## Data Manipulation

- **Inserting Data:**
- `INSERT VALUES`: Inserts a single row of data
- `INSERT SELECT`: Inserts data from a query result set
- `INSERT EXEC`: Inserts data from a stored procedure result set
- `SELECT INTO`: Creates a new table and inserts data from a query result set
- `BULK INSERT`: Imports data from a file into a table
- **Identity Property and Sequence Object:** Used to generate unique sequential values for primary keys
- **Deleting Data:**
- `DELETE`: Removes rows from a table based on a condition
- `TRUNCATE`: Removes all rows from a table
- **Merge Statement:** Performs insert, update, and delete operations in a single statement based on source data
