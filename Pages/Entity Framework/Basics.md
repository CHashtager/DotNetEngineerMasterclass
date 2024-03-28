# Basics

## Change-Tracker

- Mechanism that keeps track of changes to entities during their lifespan.
- Enables EF to generate SQL statements for database updates efficiently when **`SaveChanges`** is called.

### What's **`.AsNoTracking()`**?

**`.AsNoTracking()`** is a method in Entity Framework that can be applied to a query. It indicates that the entities retrieved should not be tracked by the change tracker. This is useful when you only need to read data and don't intend to modify or update it. By disabling tracking, you can improve performance as EF doesn't need to keep track of changes for entities that won't be updated.

### How does EF detect changes when you update a property value?

When you modify a property of an entity that is being tracked by the change tracker, EF compares the original property value with the new one. If there's a difference, EF marks the entity as modified. This change tracking is crucial for EF to generate the appropriate SQL statements during **`SaveChanges`**.

## Migrations

- The process of updating the database schema to match changes in the application's data model.
- **Code-First Migrations:** Automatically generates migration scripts based on changes in the code.

## **`SaveChanges()`, When & Why?**

- **When:** Called to persist changes made to entities in memory to the database.
- **Why:** Ensures changes are committed and transactions are applied to the database.

The **`SaveChanges()`** method in Entity Framework is used to persist changes made to entities in the context to the underlying database. It should be called when you want to commit changes.

**When to use:**

- After making modifications, additions, or deletions to entities in the context.
- When you're ready to persist these changes to the database.

**Why:**

- To ensure data consistency between your application and the database.
- To execute the necessary SQL statements to reflect the changes.
