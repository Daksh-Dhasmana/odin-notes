# Meta commands
- In `psql`, commands that start with a backslash (`\`) are called **meta-commands** (or slash commands). They are built-in shortcuts to manage your session, inspect your database structure, and view system info without writing raw SQL.

Here is the complete list of the most important and frequently used backslash commands categorized by what they do:

### 1. Connection & Session Commands

* **`\c database_name`** — Connect to a different database (e.g., `\c persondb`).
* **`\c database_name username`** — Connect to a database as a specific user.
* **`\conninfo`** — Display information about your current database connection, user, host, and port.
* **`\q`** — Quit/exit the `psql` terminal and return to your Linux shell.

### 2. Browsing Database Objects (The "Show" Commands)

* **`\l`** — List all databases on the PostgreSQL server.
* **`\dt`** — List all tables in the current database.
* **`\d`** — List all tables, views, and sequences in the current database.
* **`\d table_name`** — Describe a specific table (shows columns, data types, constraints, and indexes).
* **`\du`** — List all database roles/users and their privileges.
* **`\df`** — List all available custom functions.
* **`\di`** — List all indexes.
* **`\dn`** — List all schemas.

### 3. Execution & Workflow Helpers

* **`\i filename`** — Execute/run an external SQL script file (e.g., `\i setup.sql`).
* **`\e`** — Open your system text editor (like Nano or Vim) to write or edit a complex SQL query. When you save and exit, it executes automatically.
* **`\g`** — Send the current query buffer to the server for execution (useful if you forgot a semicolon).
* **`\p`** — Print the current query buffer to the screen.
* **`\r`** — Reset/clear the query buffer (clears anything you currently have typed out).

### 4. Display & Formatting

* **`\x`** — Toggle expanded/vertical table formatting. Helpful when a table has many columns and the text wraps awkwardly across the screen.
* **`\a`** — Toggle between aligned and unaligned output mode.
* **`\H`** — Toggle HTML output mode (renders query results as an HTML table).

### 5. Help & Information

* **`\?`** — Display general help for all `psql` backslash commands.
* **`\h`** — Display syntax help for SQL commands (e.g., typing `\h CREATE TABLE` shows you the exact syntax manual right in the terminal).

## Creating a table
-  
```
create table persondb(
    id int,
    name varchar(100)
);
```
## Adding data into table
-  
```
insert into persondb values(216, "rahul");
```
- NOTE: data should be identical to row names such as id should be in int.

## Reading data from table
-  
```
select * from <table_Name>;
select <column_name> from <table_name>;
```

## Updating and Deleting data in table
- To modify or add things to an existing table *after* you have already created it, you use the **`ALTER TABLE`** command.

Here are the most common commands you will need for updating your table structure:

### 1. Add a New Column

If you forgot to include a column (like an email or phone number) when you created the table:

```sql
ALTER TABLE person ADD COLUMN email VARCHAR(100);

```

### 2. Delete / Drop a Column

If you realize you don't need a specific column anymore:

```sql
ALTER TABLE person DROP COLUMN email;

```

### 3. Rename a Column

If you want to change the name of an existing column:

```sql
ALTER TABLE person RENAME COLUMN age TO years_old;

```

### 4. Change a Column's Data Type

If you need to expand a data type (e.g., expanding a `VARCHAR(50)` to `VARCHAR(100)`):

```sql
ALTER TABLE person ALTER COLUMN name TYPE VARCHAR(100);

```

### 5. Add a Constraint (Like `NOT NULL` or `UNIQUE`)

If you want to enforce rules on an existing column:

```sql
ALTER TABLE person ADD CONSTRAINT unique_name UNIQUE (name);

```

### 6. Drop / Remove a Constraint

If you want to remove a constraint you previously added:

```sql
ALTER TABLE person DROP CONSTRAINT unique_name;

```

---

*(Note: If you meant updating the actual data insideTo update data or modify the structure of an existing table in PostgreSQL, you use a few core commands.

Here are the most common commands you will use for updating tables, split into **updating the data inside** the table versus **updating the table structure** itself.

---

### Part 1: Updating Data Inside a Table (DML)

#### 1. Update Existing Rows (`UPDATE`)

To modify data that is already stored in your table, use the `UPDATE` command combined with `SET` and a `WHERE` clause.

* **Warning:** Always include a `WHERE` clause, or else it will update *every single row* in the table!

```sql
-- Update a person's age where their name is 'Daksh'
UPDATE person 
SET age = 22 
WHERE name = 'Daksh';

```

#### 2. Add New Data (`INSERT INTO`)

To add a new row of data to your table:

```sql
INSERT INTO person (name, age) 
VALUES ('Alex', 25);

```

#### 3. Remove Data (`DELETE`)

To delete specific rows from your table (again, always use a `WHERE` clause to avoid deleting everything):

```sql
DELETE FROM person 
WHERE name = 'Alex';

```

---

### Part 2: Updating Table Structure (DDL - `ALTER TABLE`)

If you realize you forgot a column or want to change how your table is built after creating it, you use `ALTER TABLE`.

#### 1. Add a New Column

```sql
ALTER TABLE person 
ADD COLUMN email VARCHAR(100);

```

#### 2. Delete/Drop a Column

```sql
ALTER TABLE person 
DROP COLUMN email;

```

#### 3. Rename a Column

```sql
ALTER TABLE person 
RENAME COLUMN age TO years_old;

```

#### 4. Change a Column's Data Type

```sql
ALTER TABLE person 
ALTER COLUMN name TYPE VARCHAR(100);

```

---

### Pro-Tip: Testing Safely

If you want to test an `UPDATE` or `DELETE` query to make sure it's targeting the exact rows you want before actually changing them, write it as a `SELECT` query first:

```sql
-- Run this first to check who will be affected
SELECT * FROM person WHERE name = 'Daksh';

-- If the output looks right, swap SELECT * for UPDATE...

```

## Datatype
- PostgreSQL offers a rich set of data types. When designing your tables, choosing the right type ensures your data stays clean and your queries run fast.

Here are the most common data types you will use across your full-stack projects:

### 1. Numeric Types

* **`INTEGER`** (or `INT`): Standard whole numbers (e.g., age, quantity). Range is roughly -2 billion to +2 billion.
* **`SERIAL`**: A self-incrementing 4-byte integer (1, 2, 3...). Perfect for auto-incrementing primary IDs.
* **`BIGSERIAL`**: An 8-byte auto-incrementing integer for massive tables that will have millions or billions of rows.
* **`NUMERIC(precision, scale)`** (or `DECIMAL`): Exact numbers, ideal for money and financial data where rounding errors are unacceptable.
* *Example:* `price NUMERIC(10, 2)` means up to 10 digits total, with 2 digits reserved for decimals (e.g., `99999999.99`).



### 2. Character / String Types

* **`VARCHAR(n)`**: Variable-length character string with a maximum limit (`n`). Best for names, emails, and titles where lengths vary.
* *Example:* `email VARCHAR(100)`


* **`TEXT`**: Variable-length string with *no upper limit*. Great for blog posts, comments, or long descriptions.
* **`CHAR(n)`**: Fixed-length string. If you store "AB" in a `CHAR(4)` column, PostgreSQL will pad it with two trailing spaces. (Rarely used in modern web apps).

### 3. Date and Time Types

* **`TIMESTAMP`**: Stores both date and time (e.g., `2026-11-18 21:13:00`).
* **`DATE`**: Stores just the calendar date (e.g., `2026-11-18`).
* **`TIME`**: Stores just the time of day (e.g., `21:13:00`).

### 4. Boolean Type

* **`BOOLEAN`**: Stores true/false states. It accepts `TRUE`, `FALSE`, or `NULL`.
* *Example:* `is_active BOOLEAN DEFAULT TRUE`



### 5. Special / Advanced Types (Where Postgres Shines)

* **`JSON` / `JSONB**`: Stores raw JSON data. `JSONB` (JSON Binary) is heavily preferred because it parses the data into a decomposed format, making it super fast to query nested keys. Perfect for user settings, API payloads, or flexible schemas.
* **`UUID`**: Universally Unique Identifier. A 128-bit random string (e.g., `a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11`) often used for secure, unguessable primary keys instead of sequential numbers.
* **`ARRAY`**: Allows you to store an array of values in a single column (e.g., `tags TEXT[]`).