# Introduction
- SQL (Structured Query Language) is the universal programming language used to talk to databases like PostgreSQL, MySQL, and SQLite.

# Clause
- A clause in SQL is a built-in keyword or built-in statement component used to filter, sort, group, compute, or manipulate data in database queries.

## 1) Data Manipulation Clause
  - Used for reading, filtering, grouping, and ordering data.
    - 1) `from`
      - Specifies the target table to pull data from.
      - `SELECT * FROM users;`
    - 2) `WHERE`
      -  Filters individual rows before any grouping or aggregation takes place.
      -  `SELECT * FROM users WHERE status = 'active';`
     - 3) `GROUP BY`
       -  Groups rows sharing identical column values into summary rows.
       -  `SELECT role, COUNT(*) FROM users GROUP BY role;`
      - 4) `having`
        - Filters aggregated groups generated after a GROUP BY clause.
        - `SELECT role, COUNT(*) FROM users GROUP BY role HAVING COUNT(*) > 5;`
      - 5) `order by`
        - Sorts query in ascending or descending order
        - `SELECT * FROM users ORDER BY created_at DESC;`
      - 6) `Limit/Offset`
        - Restricts the total number of returned rows and skips a specified number of initial rows.
        - `SELECT * FROM users LIMIT 10 OFFSET 20;`
        - This query retrieves 10 rows from the users table, starting at row 21 (skipping the first 20 rows).

## 2) Table Joining Clauses
- Used to combine records across two or more tables based on related columns.
 - 1) `join/on`
   - Combines rows from two tables where a specified matching condition is met.
   - `SELECT * FROM orders JOIN users ON orders.user_id = users.id;`
## 3) Data Modification Clauses
- Used alongside INSERT, UPDATE, and DELETE operations.
  - 1) `set`
    - Assigns new values to specific columns during an update operation.
    - `UPDATE users SET status = 'inactive' WHERE id = 1;`
  - 2) `VALUES`
    - Provides the raw data values to be inserted into a table.
    - `INSERT INTO users (name, email) VALUES ('Alice', 'alice@gmail.com');`

# Create Index
- `CREATE INDEX` is an SQL command used to build a dedicated, high-speed lookup structure on one or more columns of a database table.
- Its sole purpose is to make searching, filtering (WHERE), joining (JOIN), and sorting (ORDER BY) significantly faster without changing the actual data inside the table.
- Syntax
```
CREATE UNIQUE INDEX index_name 
ON table_name (column_name);
```
- Difference between primary key and create table
- ![alt text](image-2.png)