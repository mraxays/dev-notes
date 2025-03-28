# Comprehensive PostgreSQL Notes

## Table of Contents
1. [Introduction to PostgreSQL](#1-introduction-to-postgresql)  
2. [Installation & Setup](#2-installation--setup)  
3. [Basic SQL Commands](#3-basic-sql-commands)  
4. [Data Types in PostgreSQL](#4-data-types-in-postgresql)  
5. [Database & Table Management](#5-database--table-management)  
6. [Constraints & Indexes](#6-constraints--indexes)  
7. [Querying Data](#7-querying-data)  
8. [Joins & Subqueries](#8-joins--subqueries)  
9. [Views, Functions, and Procedures](#9-views-functions-and-procedures)  
10. [Transactions & Concurrency Control](#10-transactions--concurrency-control)  
11. [User Management & Security](#11-user-management--security)  
12. [Performance Optimization](#12-performance-optimization)  
13. [Extensions & Advanced Features](#13-extensions--advanced-features)  
14. [Backup & Recovery](#14-backup--recovery)  
15. [Best Practices](#15-best-practices)  

---

## 1. Introduction to PostgreSQL
**Definition:** PostgreSQL is an advanced, open-source relational database management system (RDBMS) known for its robustness, scalability, and support for advanced SQL features.

**History:** Initially developed in 1986 at the University of California, Berkeley, PostgreSQL has evolved into one of the most powerful databases, widely used in both small and enterprise applications.

**Key Features:**
- ACID compliance
- Extensibility with custom functions and operators
- Support for JSON and NoSQL-like features
- Advanced indexing techniques
- MVCC for concurrency control
- High availability with replication

---

## 2. Installation & Setup
**Installing PostgreSQL:**
```bash
# Ubuntu
sudo apt update && sudo apt install postgresql postgresql-contrib

# macOS (using Homebrew)
brew install postgresql

# Windows (via Installer)
Download from https://www.postgresql.org/download/
```

**Starting & Stopping PostgreSQL:**
```bash
# Start PostgreSQL service
sudo systemctl start postgresql

# Stop PostgreSQL service
sudo systemctl stop postgresql
```

**Accessing PostgreSQL CLI:**
```bash
sudo -u postgres psql
```

---

## 3. Basic SQL Commands
**Creating a Database:**
```sql
CREATE DATABASE mydatabase;
```

**Selecting a Database:**
```sql
\c mydatabase;
```

**Creating a Table:**
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(150) UNIQUE,
    age INT
);
```

**Inserting Data:**
```sql
INSERT INTO users (name, email, age) VALUES ('Alice', 'alice@example.com', 25);
```

**Retrieving Data:**
```sql
SELECT * FROM users;
```

**Updating Data:**
```sql
UPDATE users SET age = 26 WHERE name = 'Alice';
```

**Deleting Data:**
```sql
DELETE FROM users WHERE name = 'Alice';
```

---

## 4. Data Types in PostgreSQL
**Common Data Types:**
- `INTEGER`, `SERIAL` (Auto-incrementing integer)
- `VARCHAR(n)`, `TEXT` (String types)
- `BOOLEAN` (True/False)
- `DATE`, `TIMESTAMP`, `TIME` (Date & Time types)
- `JSON`, `JSONB` (NoSQL-like JSON support)
- `ARRAY` (Array data type)

---

## 5. Database & Table Management
**Altering a Table:**
```sql
ALTER TABLE users ADD COLUMN phone VARCHAR(15);
```

**Dropping a Table:**
```sql
DROP TABLE users;
```

**Truncating a Table (removes all data):**
```sql
TRUNCATE TABLE users;
```

---

## 6. Constraints & Indexes
**Common Constraints:**
- `PRIMARY KEY` (Ensures unique identifier)
- `UNIQUE` (Prevents duplicate values)
- `NOT NULL` (Ensures a column cannot be NULL)
- `FOREIGN KEY` (Maintains referential integrity)

**Creating an Index:**
```sql
CREATE INDEX idx_users_email ON users(email);
```

**Dropping an Index:**
```sql
DROP INDEX idx_users_email;
```

---

## 7. Querying Data
**Filtering Data:**
```sql
SELECT * FROM users WHERE age > 20;
```

**Sorting Data:**
```sql
SELECT * FROM users ORDER BY age DESC;
```

**Limiting Results:**
```sql
SELECT * FROM users LIMIT 5;
```

---

## 8. Joins & Subqueries
**INNER JOIN:**
```sql
SELECT users.name, orders.total_amount FROM users
JOIN orders ON users.id = orders.user_id;
```

**LEFT JOIN:**
```sql
SELECT users.name, orders.total_amount FROM users
LEFT JOIN orders ON users.id = orders.user_id;
```

**Subquery Example:**
```sql
SELECT name FROM users WHERE id IN (SELECT user_id FROM orders WHERE total_amount > 500);
```

---

## 9. Views, Functions, and Procedures
**Creating a View:**
```sql
CREATE VIEW user_orders AS
SELECT users.name, orders.total_amount FROM users
JOIN orders ON users.id = orders.user_id;
```

**Creating a Function:**
```sql
CREATE FUNCTION get_user_count() RETURNS INT AS $$
    SELECT COUNT(*) FROM users;
$$ LANGUAGE SQL;
```

**Calling a Function:**
```sql
SELECT get_user_count();
```

---

## 10. Transactions & Concurrency Control
**Using Transactions:**
```sql
BEGIN;
UPDATE users SET age = 27 WHERE id = 1;
COMMIT;
```

**Rolling Back a Transaction:**
```sql
BEGIN;
DELETE FROM users;
ROLLBACK;
```

---

## 11. User Management & Security
**Creating a User:**
```sql
CREATE USER newuser WITH PASSWORD 'password';
```

**Granting Permissions:**
```sql
GRANT ALL PRIVILEGES ON DATABASE mydatabase TO newuser;
```

**Revoking Permissions:**
```sql
REVOKE ALL PRIVILEGES ON DATABASE mydatabase FROM newuser;
```

---

## 12. Performance Optimization
**Using EXPLAIN for Query Analysis:**
```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE age > 30;
```

**Vacuuming the Database:**
```sql
VACUUM ANALYZE;
```

---

## 13. Extensions & Advanced Features
**Enabling an Extension:**
```sql
CREATE EXTENSION IF NOT EXISTS hstore;
```

**Using JSONB Data Type:**
```sql
SELECT data->'name' FROM users_json WHERE data->>'age' = '30';
```

---

## 14. Backup & Recovery
**Backing Up a Database:**
```bash
pg_dump mydatabase > backup.sql
```

**Restoring a Database:**
```bash
psql mydatabase < backup.sql
```

---

## 15. Best Practices
- Use **indexes** wisely to optimize queries.
- Avoid **select *** in production queries.
- Regularly **vacuum** and **analyze** the database.
- Use **parameterized queries** to prevent SQL injection.
- Implement **proper error handling** in applications.

---

## Happy Coding with PostgreSQL!

