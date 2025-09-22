# Data Engineering Interview Preparation  

This repository is a **structured guide** to prepare for Data Engineering and related technical interviews.  
It includes categorized topics, a main index, and detailed **questions & answers** for SQL and beyond.  

---

## 📑 Table of Contents  

1. [Categories](#categories)  
2. [Usage](#usage)  
3. [SQL Interview Questions](#sql-interview-questions)  
   - [A. Basics / Fundamentals](#a-basics--fundamentals)  
   - [B. Intermediate / Querying & Data Manipulation](#b-intermediate--querying--data-manipulation)  
   - [C. Advanced Topics / Performance & Design / ETL](#c-advanced-topics--performance--design--etl)  
   - [D. Scenario / Problem-Based / Real-World](#d-scenario--problem-based--real-world)  
   - [E. Very Advanced / Senior Level](#e-very-advanced--senior-level)  
   - [F. Additional / 2025 Trends](#f-additional--2025-trends)  

---

## Categories  

### 1. Foundational Skills  
- SQL  
- Programming (Python, Java, Scala, etc.)  

### 2. Data Modeling & Warehousing  
- Database design principles  
- Normalization & denormalization  
- Star & snowflake schemas  
- OLTP vs OLAP  

### 3. Big Data Technologies & Frameworks  
- Hadoop ecosystem  
- Spark  
- Hive, Pig, Impala  
- Presto, Trino  

### 4. Data Processing & Transformation (ETL/ELT)  
- Batch processing  
- ETL vs ELT design considerations  
- Data quality & validation  
- Transformation techniques  

### 5. Data Streaming & Real-Time Processing  
- Kafka  
- Flink  
- Spark Streaming  
- Pub/Sub models  

### 6. Data Orchestration & Pipelines  
- Apache Airflow  
- Luigi  
- Prefect  
- Workflow design patterns  

### 7. Cloud Platforms & DevOps for Data  
- AWS, GCP, Azure services for data  
- Infrastructure as Code (Terraform, CloudFormation)  
- CI/CD for data pipelines  
- Monitoring & observability  

### 8. System Design & Architecture  
- Designing scalable data systems  
- Data lake vs data warehouse vs lakehouse  
- Partitioning & sharding  
- High availability & fault tolerance  

### 9. Behavioral & Situational Questions  
- Past project experiences  
- Team collaboration & communication  
- Handling failures in pipelines  
- Problem-solving approaches  

---

## Usage  

Use this repository as a **structured roadmap** for interview prep.  
Each category can be expanded with:  

- Detailed notes  
- Example questions  
- Practice exercises  

---

## SQL Interview Questions  

Below are categorized **SQL interview questions and answers** for data engineers.  

---

## A. Basics / Fundamentals

### **1. What is SQL, and what role does it play in relational databases?**

**Answer:**
SQL, or *Structured Query Language*, is the standard language used to interact with relational databases. It allows us to define data structures (using DDL), manipulate data (using DML), control access (using DCL), and manage transactions (using TCL).

In relational databases, SQL acts as the interface between the user and the data. It allows us to:

* **Query data** (SELECT)
* **Modify data** (INSERT, UPDATE, DELETE)
* **Define schemas** (CREATE, ALTER, DROP)
* **Control transactions** (COMMIT, ROLLBACK)
* **Enforce security** (GRANT, REVOKE)

In short: SQL provides a consistent and declarative way to store, retrieve, and manipulate structured data.

---

### **2. What are the different categories of SQL statements (DDL, DML, DCL, TCL), and what are their use cases?** ([Caltech Bootcamps][1])

**Answer:**
SQL is categorized into four main types:

1. **DDL (Data Definition Language):** Defines and modifies schema objects.

   * Examples: `CREATE`, `ALTER`, `DROP`, `TRUNCATE`.
   * Use case: Creating a new table, altering a column type, dropping an index.

2. **DML (Data Manipulation Language):** Works with the data itself.

   * Examples: `INSERT`, `UPDATE`, `DELETE`, `SELECT`.
   * Use case: Inserting new records, updating prices, retrieving records.

3. **DCL (Data Control Language):** Manages access permissions.

   * Examples: `GRANT`, `REVOKE`.
   * Use case: Granting SELECT access on a table to a specific role.

4. **TCL (Transaction Control Language):** Manages transactions for consistency.

   * Examples: `COMMIT`, `ROLLBACK`, `SAVEPOINT`.
   * Use case: Rolling back a transaction if an error occurs during a batch insert.

---

### **3. What are primary keys, foreign keys, and unique keys, and how do they differ from one another?** ([360digitmg.com][2])

**Answer:**

* **Primary Key:**

  * A column (or set of columns) that uniquely identifies each row in a table.
  * Cannot contain NULL values.
  * Only one primary key is allowed per table.

* **Unique Key:**

  * Ensures all values in the column(s) are unique.
  * Unlike primary keys, unique keys *can* contain a single NULL value (in most RDBMS).
  * A table can have multiple unique keys.

* **Foreign Key:**

  * Establishes a link between two tables.
  * It references the primary key of another table to enforce referential integrity.
  * Use case: Orders table referencing the Customers table.

**Difference summary:** Primary key = main unique identifier, Unique key = alternate identifiers, Foreign key = relationship enforcer.

---

### **4. What are the common SQL data types, and when should each be used?** ([DataCamp][3])

**Answer:**

* **CHAR(n):** Fixed-length string. Efficient for uniform values (e.g., country codes like "US").
* **VARCHAR(n):** Variable-length string. Best for text where length varies (e.g., names, emails).
* **INT / BIGINT:** Whole numbers. Use INT for smaller ranges (like age), BIGINT for large ranges (like transaction IDs).
* **DECIMAL(p, s):** Exact numeric values with precision and scale. Ideal for monetary values.
* **FLOAT / DOUBLE:** Approximate numeric values, useful for scientific calculations but not for precise amounts.
* **DATE / DATETIME / TIMESTAMP:** Stores dates and times. TIMESTAMP often includes timezone tracking.
* **BOOLEAN (or BIT):** True/False values.

---

### **5. What is normalization, what are the different normal forms, and what are the trade-offs of denormalization?** ([360digitmg.com][2])

**Answer:**
**Normalization** is the process of organizing database tables to reduce redundancy and improve data integrity.

* **1NF:** Eliminate repeating groups, ensure atomic columns.
* **2NF:** 1NF + remove partial dependency (non-key attribute depends only on part of a composite key).
* **3NF:** 2NF + remove transitive dependencies (non-key depends only on key, not another non-key).
* **BCNF (Boyce-Codd NF):** Stricter form of 3NF.

**Trade-offs of Denormalization:**

* *Advantages:* Faster query performance, fewer joins.
* *Disadvantages:* Data redundancy, risk of anomalies, higher storage usage.

---

### **6. What is a SQL JOIN, what are the types, and when should each be used?** ([Datainterview.com][4])

**Answer:**
A **JOIN** combines rows from two or more tables based on related columns.

* **INNER JOIN:** Returns rows with matching values in both tables.
  *Use case: Customers with orders.*
* **LEFT JOIN:** Returns all rows from the left table + matching rows from the right.
  *Use case: All customers, even if they have no orders.*
* **RIGHT JOIN:** Opposite of LEFT JOIN. Less common.
* **FULL OUTER JOIN:** Returns all rows from both tables, matching where possible.
  *Use case: Union of all customers and orders.*
* **CROSS JOIN:** Cartesian product (all combinations).
  *Use case: Generating test data or all possible pairs.*
* **SELF JOIN:** A table joins itself.
  *Use case: Employee hierarchy within the same table.*

---

### **7. Difference between WHERE and HAVING clause?** ([Interview Query][5])

**Answer:**

* **WHERE:** Filters rows *before* grouping or aggregation. Works on individual rows.
* **HAVING:** Filters groups *after* aggregation. Works on grouped/aggregated results.

**Example:**

```sql
-- WHERE filters raw data
SELECT * FROM Orders WHERE OrderDate >= '2025-01-01';

-- HAVING filters aggregates
SELECT CustomerID, COUNT(*) 
FROM Orders
GROUP BY CustomerID
HAVING COUNT(*) > 5;
```

---

### **8. Purpose of GROUP BY and ORDER BY, and how are aggregation functions used with them?** ([DataCamp][3])

**Answer:**

* **GROUP BY:** Groups rows with the same values in specified columns into summary rows.
* **ORDER BY:** Sorts the result set by one or more columns.

**Aggregations (COUNT, SUM, AVG, MIN, MAX):** These summarize groups.

**Example:**

```sql
SELECT CustomerID, SUM(OrderAmount) AS TotalSpent
FROM Orders
GROUP BY CustomerID
ORDER BY TotalSpent DESC;
```

This shows each customer’s spending, sorted from highest to lowest.

---

### **9. Difference between UNION, UNION ALL, INTERSECT, and EXCEPT/MINUS?** ([Caltech Bootcamps][1])

**Answer:**

* **UNION:** Combines results, removes duplicates.
* **UNION ALL:** Combines results, keeps duplicates. Faster than UNION.
* **INTERSECT:** Returns only rows present in both queries.
* **EXCEPT (or MINUS in Oracle):** Returns rows from the first query that are not in the second.

---

### **10. Difference between DELETE, TRUNCATE, and DROP?** ([DataCamp][3])

**Answer:**

* **DELETE:** Removes rows one by one, can have a WHERE clause. Logged operation (slower).
* **TRUNCATE:** Removes all rows, resets table storage. Faster, cannot use WHERE.
* **DROP:** Removes the table structure entirely from the database.

---

### **11. What are SQL Views, and what are their advantages and disadvantages?** ([Datainterview.com][4])

**Answer:**
A **View** is a virtual table created by a saved query.

**Advantages:**

* Simplifies complex queries.
* Provides security by restricting column/row access.
* Helps maintain abstraction between schema and users.

**Disadvantages:**

* Performance overhead if nested or complex.
* Cannot always perform DML directly (depends on DBMS).

---

### **12. What are stored procedures, functions, and triggers in SQL, and in what scenarios should each be used?** ([Datainterview.com][4])

**Answer:**

* **Stored Procedure:** A precompiled block of SQL + logic.
  *Use case:* Encapsulating business logic like batch updates.

* **Function:** Returns a single value or table, often used in SELECT.
  *Use case:* Calculating derived fields, reusable computations.

* **Trigger:** Executes automatically in response to events (INSERT, UPDATE, DELETE).
  *Use case:* Enforcing audit trails, maintaining log tables.

---

### **13. What is a SQL Cursor, and when is it appropriate?**

**Answer:**
A **Cursor** allows row-by-row processing of query results.

**Use case:** When set-based operations aren’t possible (e.g., sequential calculations, complex business logic).

**Downside:** Cursors are slower and resource-intensive compared to set-based operations. They should be a last resort.

---

### **14. What is collation in SQL, and how does it affect character sets, sorting, and case sensitivity?**

**Answer:**
**Collation** defines rules for string comparison, including:

* **Character set encoding** (e.g., UTF-8 vs Latin1).
* **Sorting rules** (alphabetical order, locale-specific).
* **Case sensitivity** (e.g., `A = a` or not).

**Example:**

* `SQL_Latin1_General_CP1_CI_AS` → Case Insensitive, Accent Sensitive.
* Changing collation can change query results when sorting or comparing text.

---
## B. Intermediate / Querying & Data Manipulation

### **15. How can you identify duplicate rows in a table, and how would you delete duplicates while keeping only one instance?** ([vishalbarvaliya.com][6])

**Answer:**
To identify duplicates, we can use `GROUP BY` with `HAVING COUNT(*) > 1`.

**Example (identify):**

```sql
SELECT name, department, COUNT(*)
FROM Employees
GROUP BY name, department
HAVING COUNT(*) > 1;
```

To delete duplicates while keeping one, we can use a **window function** with `ROW_NUMBER()`:

```sql
WITH duplicates AS (
    SELECT 
        id, 
        ROW_NUMBER() OVER (PARTITION BY name, department ORDER BY id) AS row_num
    FROM Employees
)
DELETE FROM duplicates WHERE row_num > 1;
```

This way, we keep the first occurrence (row\_num = 1) and remove others.

---

### **16. How can you retrieve the *nth highest salary* (e.g., the second highest) from a salary table?** ([Datainterview.com][4])

**Answer:**
There are multiple approaches.

**Method 1: Using `LIMIT`/`OFFSET` (MySQL/Postgres):**

```sql
SELECT DISTINCT salary
FROM Employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;  -- second highest
```

**Method 2: Using subquery:**

```sql
SELECT MAX(salary)
FROM Employees
WHERE salary < (SELECT MAX(salary) FROM Employees);
```

**Method 3: Using window functions:**

```sql
SELECT salary
FROM (
  SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
  FROM Employees
) t
WHERE rnk = 2;
```

The window function method is more robust for ties.

---

### **17. How can you retrieve the latest record for each group (e.g., the most recent timestamp per user)?** ([bigtechinterviews.com][7])

**Answer:**
We can use `ROW_NUMBER()` partitioned by the group and ordered by timestamp.

```sql
SELECT user_id, action, timestamp
FROM (
    SELECT *,
           ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY timestamp DESC) AS rn
    FROM UserActions
) t
WHERE rn = 1;
```

This ensures one latest record per user.

Alternative: a `JOIN` with a subquery that selects the `MAX(timestamp)` per user.

---

### **18. What are subqueries in SQL, and how do correlated subqueries differ from non-correlated ones?** ([Datainterview.com][4])

**Answer:**

* A **subquery** is a query nested inside another query (in `SELECT`, `FROM`, or `WHERE`).

**Non-correlated subquery:** Independent of the outer query.

```sql
SELECT name 
FROM Employees
WHERE salary > (SELECT AVG(salary) FROM Employees);
```

**Correlated subquery:** Depends on values from the outer query; runs once per row.

```sql
SELECT e1.name
FROM Employees e1
WHERE salary > (SELECT AVG(salary) 
                FROM Employees e2
                WHERE e1.department_id = e2.department_id);
```

So, non-correlated runs once, correlated runs row-by-row.

---

### **19. What are Common Table Expressions (CTEs) in SQL, and how do they compare to subqueries?** ([Interview Query][5])

**Answer:**
A **CTE** is a temporary named result set defined using `WITH`.

**Example:**

```sql
WITH HighEarners AS (
    SELECT name, salary
    FROM Employees
    WHERE salary > 100000
)
SELECT * FROM HighEarners WHERE name LIKE 'A%';
```

**Comparison:**

* **CTEs** improve readability and allow reuse within the query.
* Subqueries can be harder to read if deeply nested.
* CTEs support recursion, which subqueries cannot.

---

### **20. What are SQL window functions (e.g., ROW\_NUMBER, RANK, DENSE\_RANK, LEAD, LAG), and when would you use them?** ([Datainterview.com][4])

**Answer:**
Window functions perform calculations across sets of rows *without collapsing them*.

* **ROW\_NUMBER():** Assigns a unique sequence.
* **RANK():** Allows gaps in ranking (1, 2, 2, 4).
* **DENSE\_RANK():** No gaps in ranking (1, 2, 2, 3).
* **LEAD() / LAG():** Access next/previous row values.

**Use cases:**

* Ranking salaries per department.
* Finding trends (compare today vs yesterday).
* Deduplicating rows.

Example:

```sql
SELECT name, salary,
       RANK() OVER (ORDER BY salary DESC) AS rnk
FROM Employees;
```

---

### **21. How do self-joins, hierarchical queries, and recursive queries work in SQL?** ([Wikipedia][8])

**Answer:**

* **Self-join:** A table joins itself.
  Example: finding employees and their managers from the same Employee table.

  ```sql
  SELECT e.name AS Employee, m.name AS Manager
  FROM Employees e
  JOIN Employees m ON e.manager_id = m.id;
  ```

* **Hierarchical queries:** Used to traverse parent-child structures. Some DBs (like Oracle) use `CONNECT BY` for hierarchy.

* **Recursive queries (via CTE):** Allow traversing hierarchies across multiple levels.

  ```sql
  WITH RECURSIVE OrgChart AS (
      SELECT id, name, manager_id
      FROM Employees
      WHERE manager_id IS NULL
      UNION ALL
      SELECT e.id, e.name, e.manager_id
      FROM Employees e
      JOIN OrgChart oc ON e.manager_id = oc.id
  )
  SELECT * FROM OrgChart;
  ```

---

### **22. How do you perform pivot and unpivot operations in SQL, and when are they useful?** ([Datainterview.com][4])

**Answer:**

* **Pivot:** Rotate rows into columns. Useful for reporting.

```sql
SELECT department,
       SUM(CASE WHEN gender = 'M' THEN 1 ELSE 0 END) AS MaleCount,
       SUM(CASE WHEN gender = 'F' THEN 1 ELSE 0 END) AS FemaleCount
FROM Employees
GROUP BY department;
```

* Some DBs support `PIVOT` syntax directly (SQL Server, Oracle).

* **Unpivot:** Convert columns into rows. Useful for normalizing wide tables.

```sql
SELECT EmployeeID, Attribute, Value
FROM Employees
UNPIVOT (Value FOR Attribute IN (Phone, Email, Address)) AS unpvt;
```

---

### **23. How can you implement conditional logic in SQL using CASE expressions?** ([DataCamp][3])

**Answer:**
The `CASE` expression allows if-else logic.

**Example:**

```sql
SELECT name,
       salary,
       CASE 
           WHEN salary > 100000 THEN 'High'
           WHEN salary BETWEEN 50000 AND 100000 THEN 'Medium'
           ELSE 'Low'
       END AS SalaryLevel
FROM Employees;
```

Use cases: bucketing, conditional aggregations, transforming values.

---

### **24. What are temporary tables, derived tables, and table variables, and how do they differ?** ([Datainterview.com][4])

**Answer:**

* **Temporary Tables:** Created with `CREATE TEMP TABLE` or `#TableName`. Persist for the session. Good for intermediate storage.
* **Derived Tables:** Subqueries in the `FROM` clause. Exist only for the query execution.
* **Table Variables (SQL Server):** Variables that hold table-like structures. Scope-limited.

**Difference:** Temporary tables persist across queries in a session; derived tables don’t; table variables are more lightweight but with limited features.

---

### **25. What is dynamic SQL, and what are the advantages and disadvantages of constructing queries at runtime?**

**Answer:**
**Dynamic SQL** is SQL code built and executed as a string at runtime.

**Example:**

```sql
DECLARE @sql NVARCHAR(MAX);
SET @sql = 'SELECT * FROM Employees WHERE department = ''' + @dept + '''';
EXEC sp_executesql @sql;
```

**Advantages:**

* Flexible, handles variable table/column names.
* Useful for building parameterized reports.

**Disadvantages:**

* Risk of SQL injection if not parameterized.
* Harder to debug and maintain.
* Potential performance issues (execution plan not reused).

---

### **26. What are the common SQL functions for string parsing and manipulation, and how can you use pattern matching or regex in SQL?**

**Answer:**

* **String functions:**

  * `SUBSTRING()`, `LEFT()`, `RIGHT()`, `LEN()`/`LENGTH()`.
  * `TRIM()`, `LTRIM()`, `RTRIM()`.
  * `CONCAT()`.
  * `REPLACE()`, `CHARINDEX()` / `INSTR()`.

* **Pattern Matching:**

  * `LIKE '%pattern%'`.
  * Wildcards: `%` (any), `_` (single character).

* **Regex:**

  * Supported in some DBs:

    * Postgres: `~` (regex match).
    * MySQL: `REGEXP`.

**Example:**

```sql
SELECT name FROM Employees
WHERE email REGEXP '^[A-Za-z0-9._%+-]+@company\\.com$';
```

---

### **27. What are the different techniques for implementing pagination in SQL queries?**

**Answer:**
Pagination is retrieving results in chunks/pages.

* **LIMIT + OFFSET (Postgres, MySQL):**

```sql
SELECT * FROM Employees ORDER BY id LIMIT 10 OFFSET 20;
```

* **ROW\_NUMBER() approach:**

```sql
WITH ordered AS (
  SELECT *, ROW_NUMBER() OVER (ORDER BY id) AS rn
  FROM Employees
)
SELECT * FROM ordered WHERE rn BETWEEN 21 AND 30;
```

* **Keyset pagination (efficient for large datasets):**

```sql
SELECT * FROM Employees
WHERE id > last_seen_id
ORDER BY id
LIMIT 10;
```

Keyset pagination is better for performance because it avoids skipping rows with OFFSET.

---

## C. Advanced Topics / Performance & Design / ETL

### **28. What are indexes in SQL, what are the different types (clustered, non-clustered, composite), and when should they be used?** ([Caltech Bootcamps][1])

**Answer:**
An **index** is a database structure that improves the speed of data retrieval operations at the cost of additional storage and slower writes.

**Types:**

* **Clustered Index:**

  * Determines the physical order of rows in a table.
  * Only one clustered index per table (usually on the primary key).
  * Example: Employees ordered by `EmployeeID`.

* **Non-Clustered Index:**

  * A separate structure that points to the data row.
  * Multiple non-clustered indexes allowed.
  * Example: Index on `LastName` to search employees quickly.

* **Composite Index:**

  * Index on multiple columns.
  * Order of columns matters (`INDEX(col1, col2)`).
  * Example: Index on `(DepartmentID, Salary)` to speed up queries filtering both.

**Use case:**
Indexes should be used for frequently queried columns, join keys, and filter conditions. Over-indexing should be avoided due to storage and slower `INSERT/UPDATE/DELETE`.

---

### **29. How do you analyze and optimize a SQL query using execution plans, and what techniques can reduce full table scans and improve performance?** ([Interview Query][5])

**Answer:**

* **Execution Plan:** Shows how the database engine executes a query (order of joins, index usage, cost estimates).

  * In SQL Server: `EXPLAIN` or `SET SHOWPLAN_ALL`.
  * In Postgres/MySQL: `EXPLAIN ANALYZE`.

**Optimization techniques:**

1. Create appropriate indexes (especially on JOIN, WHERE, ORDER BY).
2. Avoid `SELECT *`, only retrieve required columns.
3. Rewrite subqueries as joins if more efficient.
4. Use partitioning to reduce scanned data.
5. Use proper join strategies (HASH JOIN, MERGE JOIN, etc.).
6. Avoid functions on indexed columns (`WHERE YEAR(date) = 2025` breaks index use).

Example:

```sql
EXPLAIN SELECT * FROM Orders WHERE CustomerID = 100;
```

This will show if an index is used or if a full table scan occurs.

---

### **30. What is database partitioning (horizontal and vertical), and what is sharding? When are these techniques useful?** ([Datainterview.com][4])

**Answer:**

* **Horizontal Partitioning:** Splitting rows into partitions based on values.
  Example: Orders partitioned by `OrderDate` (2024 orders in one partition, 2025 in another).

* **Vertical Partitioning:** Splitting columns into different tables.
  Example: Storing large text fields in a separate table while keeping frequently accessed columns in the main table.

* **Sharding:** Distributing partitions across multiple physical servers.
  Example: User data split by region across different servers (US shard, EU shard).

**Use cases:** Improve query performance, reduce contention, and scale out databases for very large datasets.

---

### **31. What are materialized views and indexed views, and how do they improve query performance?** ([Datainterview.com][4])

**Answer:**

* **Materialized View:** A stored, precomputed query result.

  * Can be refreshed manually or automatically.
  * Use case: Pre-aggregated sales totals by month.

* **Indexed View (SQL Server, Oracle):** A view that has a physical index built on it.

  * Acts like a materialized view, but fully maintained by the system.

**Benefits:**

* Reduce computation at query time.
* Speed up complex joins and aggregations.

**Example:**

```sql
CREATE MATERIALIZED VIEW monthly_sales AS
SELECT customer_id, SUM(amount) AS total
FROM Orders
GROUP BY customer_id;
```

---

### **32. What are transactions in SQL, what do the ACID properties mean, and how do isolation levels affect concurrency?** ([360digitmg.com][2])

**Answer:**

* **Transaction:** A unit of work executed as a whole (`BEGIN`, `COMMIT`, `ROLLBACK`).

* **ACID properties:**

  * **Atomicity:** All operations succeed or none.
  * **Consistency:** Ensures data integrity.
  * **Isolation:** Transactions don’t interfere improperly.
  * **Durability:** Committed changes are permanent.

* **Isolation Levels:**

  * **Read Uncommitted:** Can see uncommitted changes (dirty reads).
  * **Read Committed:** Prevents dirty reads (default in most DBs).
  * **Repeatable Read:** Prevents non-repeatable reads.
  * **Serializable:** Strictest, ensures full consistency.

Trade-off: Higher isolation reduces concurrency and increases locking.

---

### **33. How do you design SQL queries for ETL or data pipelines, and what are the differences between incremental and full load strategies?** ([Interview Query][5])

**Answer:**

* **ETL SQL Queries:** Typically involve extracting from source tables, transforming (joins, filters, aggregations), and loading into target tables.

* **Full Load:** Reloads entire dataset every run.

  * Simple, but expensive for large data.

* **Incremental Load:** Only loads new or changed records.

  * Requires tracking mechanism (timestamps, change-data-capture, or surrogate keys).
  * Example:

    ```sql
    INSERT INTO TargetTable
    SELECT * FROM SourceTable
    WHERE updated_at > last_run_timestamp;
    ```

**Data engineers usually prefer incremental loads for efficiency.**

---

### **34. How do you approach database schema design in SQL, and what are the trade-offs between star schema and snowflake schema?** ([Datainterview.com][4])

**Answer:**

* **Schema Design:**

  * Normalize for OLTP systems (reduce redundancy).
  * Denormalize for OLAP systems (optimize queries).

* **Star Schema:**

  * Central fact table + denormalized dimension tables.
  * Simpler, faster joins, common in data warehouses.

* **Snowflake Schema:**

  * Dimensions normalized into multiple related tables.
  * Saves space, more flexible, but queries require more joins.

**Trade-off:** Star = performance, Snowflake = storage efficiency and consistency.

---

### **35. What techniques can you use to optimize queries on very large tables, such as partition pruning or parallel processing?** ([Interview Query][5])

**Answer:**

* **Partition Pruning:** Only scan relevant partitions (e.g., `WHERE order_date >= '2025-01-01'`).
* **Indexing:** Use covering indexes to reduce lookups.
* **Parallel Query Execution:** Allow multiple threads/nodes to scan partitions in parallel.
* **Columnar Storage:** Use columnar databases for analytics (Redshift, BigQuery).
* **Materialized Views/Pre-aggregation:** Reduce runtime calculations.

---

### **36. How does SQL handle NULL values, what is three-valued logic, and how do NULLs affect joins and aggregations?** ([360digitmg.com][2])

**Answer:**

* **NULL:** Represents unknown or missing values.

* **Three-Valued Logic:** Any comparison with NULL can be `TRUE`, `FALSE`, or `UNKNOWN`.
  Example: `NULL = 5` → `UNKNOWN`.

* **Effects:**

  * `WHERE col = NULL` → No rows (use `IS NULL`).
  * Joins: Rows with NULL in join key don’t match.
  * Aggregations: `COUNT(col)` ignores NULLs, but `COUNT(*)` counts all rows.

---

### **37. What are common SQL security issues such as SQL injection, and how do permissions, roles, and data masking mitigate them?**

**Answer:**

* **SQL Injection:** Malicious input alters query logic.
  Example: `' OR 1=1 --` in a login field.

**Mitigations:**

* Use parameterized queries/prepared statements.
* Restrict access with **roles/permissions** (principle of least privilege).
* **Data masking:** Show partial sensitive data (e.g., only last 4 digits of SSN).
* Regular audits and input validation.

---

### **38. What are auto-increment (identity) columns in SQL, and what issues can arise with gaps, overflow, or schema migrations?**

**Answer:**

* **Auto-increment/identity:** Automatically generates sequential IDs.

**Issues:**

* **Gaps:** Deletes or rollbacks cause gaps in sequence.
* **Overflow:** INT may run out (e.g., 2 billion limit). Solution: use BIGINT.
* **Migrations:** Moving data may cause conflicts in IDs; need reseeding or sequences.

---

### **39. What are filtered or partial indexes, and how do you handle skewed data distribution in indexes or joins?**

**Answer:**

* **Filtered/Partial Index:** Indexes only a subset of rows.
  Example:

  ```sql
  CREATE INDEX idx_active_users ON Users(last_login) WHERE status = 'active';
  ```

  Useful when queries filter on a small portion of data.

* **Skewed Data:**

  * Uneven distribution can cause query imbalance.
  * Mitigation: histograms, indexed views, partitioning, or hints to the optimizer.

---

### **40. How should you store and query large objects such as text, JSON, XML, or BLOB data in SQL databases?**

**Answer:**

* **Text:** Use `TEXT`/`CLOB`. For search, use full-text indexes.
* **JSON/XML:**

  * Many DBs (Postgres, MySQL, SQL Server) support JSON/XML types with functions.
  * Example: `JSON_EXTRACT()` in MySQL, `->` operator in Postgres.
* **BLOBs (Binary Large Objects):** Best stored in object storage (S3, GCS), with only references in DB for performance.

---

### **41. How can collation and character set differences affect joins, comparisons, and performance in SQL?**

**Answer:**

* **Character Set:** Defines encoding (UTF-8, Latin1).
* **Collation:** Defines rules for comparison (case sensitivity, locale).

**Effects:**

* Joins may fail if columns have different collations (`COLLATION mismatch`).
* Sorting results may differ by locale (e.g., accented characters).
* Case-sensitive collations increase index size but allow case-specific queries.

---

### **42. What are race conditions in SQL, and how can concurrent updates and writes be managed through locking and isolation levels?**

**Answer:**

* **Race Condition:** When two transactions read/update the same data concurrently, causing inconsistent results.

**Example:** Two users withdraw from the same bank account simultaneously.

**Mitigation:**

* Use appropriate **isolation levels**.
* Use **locking mechanisms**:

  * Pessimistic locking (`SELECT ... FOR UPDATE`).
  * Optimistic locking (version columns).

---

### **43. What is the “Halloween Problem” in database updates, and how is it mitigated?**

**Answer:**

* **Halloween Problem:** Occurs when an update modifies a row so it qualifies for reprocessing in the same scan.
  Example:

  ```sql
  UPDATE Employees
  SET salary = salary * 1.1
  WHERE salary < 100000;
  ```

  If indexed on salary, the same row might get updated multiple times.

**Mitigation:**

* DB engines internally use **spool (temporary storage)** to ensure each row is updated only once.
* As developers, we can also use intermediate tables or disable affected indexes during updates.

---

## D. Scenario / Problem-Based / Real-World

### **44. Given two or more tables (e.g., users, orders, products), how would you write a query to produce metrics such as the top 3 products by revenue per month or the average order size per user over the last 3 months?**

**Answer:**
This question tests ability to combine tables, aggregate, and filter with time windows.

* **Top 3 products by revenue per month:**

```sql
SELECT 
    DATE_TRUNC('month', o.order_date) AS month,
    p.product_id,
    SUM(o.quantity * p.price) AS revenue,
    RANK() OVER (PARTITION BY DATE_TRUNC('month', o.order_date) 
                 ORDER BY SUM(o.quantity * p.price) DESC) AS rnk
FROM Orders o
JOIN Products p ON o.product_id = p.product_id
GROUP BY month, p.product_id
HAVING SUM(o.quantity * p.price) > 0
QUALIFY rnk <= 3;  -- In Snowflake/BigQuery. In Postgres: wrap in subquery.
```

* **Average order size per user (last 3 months):**

```sql
SELECT 
    u.user_id,
    AVG(o.total_amount) AS avg_order_size
FROM Users u
JOIN Orders o ON u.user_id = o.user_id
WHERE o.order_date >= CURRENT_DATE - INTERVAL '3 months'
GROUP BY u.user_id;
```

**Key skills demonstrated:** Joins, aggregations, window functions, time filtering.

---

### **45. How would you design a database schema for clickstream or event data, and what sample queries could you write to calculate metrics such as session duration or bounce rate?**

**Answer:**

* **Schema Design (fact table approach):**

  ```sql
  CREATE TABLE Events (
      event_id BIGINT PRIMARY KEY,
      user_id BIGINT,
      session_id BIGINT,
      event_type VARCHAR(50),
      event_time TIMESTAMP,
      page_url TEXT,
      referrer_url TEXT,
      device_type VARCHAR(20)
  );
  ```

* **Session Duration:**

```sql
SELECT 
    session_id,
    user_id,
    MAX(event_time) - MIN(event_time) AS session_duration
FROM Events
GROUP BY session_id, user_id;
```

* **Bounce Rate (sessions with only one event):**

```sql
SELECT 
    COUNT(CASE WHEN event_count = 1 THEN 1 END) * 1.0 / COUNT(*) AS bounce_rate
FROM (
    SELECT session_id, COUNT(*) AS event_count
    FROM Events
    GROUP BY session_id
) t;
```

**Rationale:** Schema should be append-only, optimized for time-series queries, with indexing on `(user_id, session_id, event_time)`.

---

### **46. Given a table with events and timestamps, how would you detect missing data or identify gaps (e.g., days with no events or the longest streak of inactivity per user)?**

**Answer:**

* **Days with no events:** Use a calendar/date dimension.

```sql
SELECT d.calendar_date
FROM Calendar d
LEFT JOIN Events e ON d.calendar_date = DATE(e.event_time)
WHERE e.event_time IS NULL;
```

* **Longest inactivity streak per user:** Use `LAG()` to compare consecutive event dates.

```sql
SELECT 
    user_id,
    MAX(event_time - LAG(event_time) OVER (PARTITION BY user_id ORDER BY event_time)) AS longest_gap
FROM Events;
```

This identifies gaps between events per user.

---

### **47. Given raw logs or messy input data, how would you write SQL queries to clean or transform the data (e.g., map codes, parse strings, deduplicate rows, and join with lookup tables)?**

**Answer:**

* **Mapping codes with lookup table:**

```sql
SELECT e.event_id, e.user_id, l.code_description
FROM RawEvents e
JOIN CodeLookup l ON e.code = l.code;
```

* **Parsing strings (Postgres example):**

```sql
SELECT 
    SPLIT_PART(raw_message, '|', 1) AS field1,
    SPLIT_PART(raw_message, '|', 2) AS field2
FROM RawLogs;
```

* **Deduplicating rows:**

```sql
SELECT DISTINCT * FROM RawLogs;
-- Or use ROW_NUMBER() and delete duplicates
```

**Approach:** ETL SQL should progressively clean in staging tables before loading into production fact tables.

---

### **48. In an ETL scenario, how would you implement incremental load logic, identify changed rows, and handle late-arriving data?**

**Answer:**

* **Incremental load:** Track last load timestamp.

```sql
INSERT INTO TargetTable
SELECT * 
FROM SourceTable
WHERE updated_at > last_load_time;
```

* **Identify changed rows:** Use **CDC (Change Data Capture)** or hash comparison.

```sql
SELECT * 
FROM Source s
LEFT JOIN Target t ON s.id = t.id
WHERE s.hash_val <> t.hash_val OR t.id IS NULL;
```

* **Late-arriving data:** Use **upserts (MERGE statements)** to handle delayed records.

```sql
MERGE INTO Target t
USING Source s
ON t.id = s.id
WHEN MATCHED THEN UPDATE SET t.col = s.col
WHEN NOT MATCHED THEN INSERT VALUES (s.id, s.col);
```

---

### **49. If a SQL query or pipeline is running slowly, how would you diagnose performance issues by analyzing the schema, indexes, and execution plan, and what improvements would you suggest?**

**Answer:**
**Steps:**

1. **Check execution plan:** Look for full table scans, nested loops, missing indexes.
2. **Schema review:** Ensure keys and datatypes are correct.
3. **Index analysis:** Are queries using indexes or causing index scans instead of seeks?
4. **Rewrite queries:** Avoid unnecessary subqueries, use window functions instead of self-joins.
5. **Partition pruning:** Ensure filters match partition keys.
6. **Caching/Materialized Views:** Precompute heavy aggregations.

**Example improvement:**
Changing

```sql
WHERE YEAR(order_date) = 2025
```

to

```sql
WHERE order_date BETWEEN '2025-01-01' AND '2025-12-31'
```

so the index on `order_date` is used.

---

### **50. How would you approach migrating a database schema or data, ensuring version control and backward compatibility?**

**Answer:**

* **Schema migration strategy:**

  * Use tools like Liquibase, Flyway, or Alembic (for versioned migrations).
  * Maintain migration scripts in source control.
  * Apply changes in small, reversible steps (e.g., add new column before dropping old).

* **Backward compatibility:**

  * Deploy schema changes before application code changes (expand-contract pattern).
  * Keep old columns until consumers are migrated.
  * Run dual writes temporarily.

* **Data migration:**

  * Migrate in batches to avoid downtime.
  * Validate with checksums or row counts.

---

### **51. How would you design SQL systems for scale, including partitioning, archiving, compressing, and summarizing large tables, and when would you denormalize?**

**Answer:**

* **Partitioning:**

  * Horizontal partitioning by time (e.g., monthly sales).
  * Improves query performance by pruning irrelevant partitions.

* **Archiving:**

  * Move cold data to cheaper storage (separate archive tables, or S3).
  * Keep recent data in fast storage.

* **Compression:**

  * Use columnar storage + compression (e.g., Parquet, ORC).
  * Reduces I/O significantly for analytical queries.

* **Summarization:**

  * Precompute aggregates into summary tables (daily revenue, monthly active users).

* **Denormalization:**

  * Useful for read-heavy workloads like reporting (avoid multiple joins).
  * Trade-off: storage and update anomalies.

**Example:** Fact tables in a warehouse might be denormalized into a star schema for BI performance.

---

✅ That covers **44–51** in full interview style, with clear reasoning and examples.

Would you like me to now **bundle Q1–Q51 into a single “SQL Interview Master Guide” document (structured by category: basics → advanced → applied/data engineering use cases)** so you have one comprehensive prep resource?




---

## E. Very Advanced / Senior Level

### **52. How do distributed SQL and big data SQL engines (Hive, Presto, Athena, BigQuery, Spark SQL) differ, and what factors should you consider when using them?**

**Answer:**
These engines allow SQL over large, distributed datasets, but they differ in **execution model, latency, cost, and ecosystem**.

* **Hive:**

  * SQL-on-Hadoop. Batch-oriented (MapReduce or Tez/Spark).
  * High latency, good for ETL.

* **Presto/Trino:**

  * Distributed query engine optimized for low-latency interactive queries.
  * Federated queries across multiple sources.

* **Athena:**

  * Serverless Presto on AWS S3. Pay-per-query. Great for ad-hoc analysis.

* **BigQuery:**

  * Fully managed, serverless, columnar data warehouse.
  * Pay-per-query with massive parallelism.

* **Spark SQL:**

  * Part of Apache Spark. Supports batch and streaming, integrates with ML.
  * More flexible for pipelines but heavier than Presto.

**Factors to consider:**

* Query latency (ad-hoc vs batch).
* Cost model (per-query vs cluster).
* Data format support (Parquet, ORC, JSON).
* Ecosystem (integration with BI tools, ML frameworks).

---

### **53. How can you handle semi-structured data (JSON, XML, nested data) in SQL, including querying and indexing?**

**Answer:**

* **Storage:** Modern SQL engines (Postgres, MySQL, SQL Server, BigQuery) support JSON/XML types.

* **Querying JSON (Postgres):**

```sql
SELECT user_id, details->>'country' AS country
FROM Events
WHERE details->>'device' = 'mobile';
```

* **Querying XML (SQL Server):**

```sql
SELECT event_data.value('(/event/user)[1]', 'VARCHAR(50)') AS user_id
FROM EventLogs;
```

* **Indexing:**

  * Postgres: GIN indexes on JSONB.
  * SQL Server: XML indexes.
  * BigQuery: Automatic optimization on nested fields.

**Best practices:** Flatten nested data in ETL if queries frequently need joins; keep semi-structured format if schema evolves rapidly.

---

### **54. How do you design SQL queries for time-series data, including windowing, retention policies, and custom aggregations?**

**Answer:**

* **Schema design:** Partition by time (daily/monthly tables). Cluster/index on timestamp.

* **Windowing (rolling averages, moving sums):**

```sql
SELECT user_id, event_time,
       AVG(value) OVER (PARTITION BY user_id ORDER BY event_time ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS rolling_avg
FROM Metrics;
```

* **Retention policies:** Drop/archive old partitions.

```sql
ALTER TABLE Metrics DROP PARTITION older_than_2023;
```

* **Custom aggregations:** Example: daily active users.

```sql
SELECT DATE(event_time) AS day, COUNT(DISTINCT user_id) AS dau
FROM Events
GROUP BY day;
```

---

### **55. How do you design schemas and queries for multi-tenant databases, and how do you enforce isolation and partitioning by tenant?**

**Answer:**
**Schema strategies:**

1. **Shared schema + tenant\_id column:**

   * All tenants share tables.
   * Enforce isolation via row-level security.
2. **Separate schema per tenant:**

   * Isolation is stronger, but schema management is complex.
3. **Separate database per tenant:**

   * Full isolation, costly to scale.

**Partitioning by tenant:** Partition tables by `tenant_id`.

**Isolation enforcement:**

* Use **row-level security (Postgres)**:

```sql
CREATE POLICY tenant_policy ON Orders
USING (tenant_id = current_setting('tenant.id')::int);
```

**Trade-offs:** Shared schema scales better; separate schemas/databases are safer for compliance-heavy industries.

---

### **56. How do you design schemas and pipelines differently for real-time versus batch processing, and what role does change data capture (CDC) play?**

**Answer:**

* **Batch Processing:**

  * ETL runs periodically (daily/hourly).
  * Schema optimized for bulk loads (fact/dim tables).

* **Real-Time Processing:**

  * Streams data continuously.
  * Schema optimized for append-only, event-based storage.

* **CDC (Change Data Capture):**

  * Captures inserts/updates/deletes in real time.
  * Used to replicate changes into streaming systems (e.g., Kafka → Spark → SQL warehouse).

**Example:** A real-time schema might store events with Kafka timestamps; batch schema stores fact tables aggregated daily.

---

### **57. How do concurrency, locking, and deadlocks impact SQL performance, and how can you design for high concurrency with safe reads/writes?**

**Answer:**

* **Concurrency:** Multiple transactions accessing data simultaneously.
* **Locking:** Ensures consistency but reduces concurrency.

  * Row-level locks: more granular, better concurrency.
  * Table locks: block all access.
* **Deadlocks:** Two transactions block each other cyclically.

**Designing for high concurrency:**

* Keep transactions short.
* Use optimistic locking (version columns).
* Choose proper isolation level (e.g., `READ COMMITTED` for most OLTP workloads).
* Use connection pooling.

**Example:**

```sql
UPDATE Accounts
SET balance = balance - 100
WHERE id = 123 AND version = 5;
```

(Only succeeds if version matches, preventing lost updates).

---

### **58. How do you implement incremental aggregation, rollups, and materialized metrics in SQL?**

**Answer:**

* **Incremental Aggregation:** Only aggregate new/changed data.

```sql
INSERT INTO DailySales (date, total_sales)
SELECT order_date, SUM(amount)
FROM Orders
WHERE order_date = CURRENT_DATE
GROUP BY order_date;
```

* **Rollups (SQL `GROUPING SETS`):**

```sql
SELECT region, product, SUM(sales)
FROM Orders
GROUP BY ROLLUP(region, product);
```

* **Materialized Metrics:** Precompute metrics in a materialized view.

```sql
CREATE MATERIALIZED VIEW monthly_sales AS
SELECT month, SUM(amount) AS total
FROM Orders
GROUP BY month;
```

**Benefit:** Avoids recomputation for dashboards.

---

### **59. How do SQL engines estimate query costs, and what are the trade-offs between computation, storage, and latency?**

**Answer:**

* **Query optimizers** estimate cost using statistics: row counts, index selectivity, histograms.
* Costs include:

  * **Computation:** CPU/memory for joins, aggregations.
  * **Storage:** I/O from scanning tables/partitions.
  * **Latency:** Query response time.

**Trade-offs:**

* Pre-aggregations save computation but increase storage.
* Denormalization improves latency but costs storage.
* Partition pruning reduces storage reads but requires design effort.

**Interview tip:** Always mention analyzing **execution plans** and **statistics maintenance**.

---

### **60. How do recursive CTEs handle hierarchical data, and what are the performance challenges and risks of cyclic dependencies?**

**Answer:**

* **Recursive CTEs:** Query hierarchical data (e.g., org charts, folder trees).

**Example:**

```sql
WITH RECURSIVE OrgChart AS (
    SELECT id, name, manager_id
    FROM Employees
    WHERE manager_id IS NULL
    UNION ALL
    SELECT e.id, e.name, e.manager_id
    FROM Employees e
    JOIN OrgChart o ON e.manager_id = o.id
)
SELECT * FROM OrgChart;
```

* **Performance challenges:**

  * Can be slow on deep hierarchies.
  * Requires careful indexing.

* **Cyclic dependency risk:** If A references B and B references A, recursion loops forever. Most DBs require a **cycle check** or recursion depth limit.

---

### **61. What are advanced indexing strategies (covering indexes, filtered indexes), and how should you maintain or rebuild indexes in large databases?**

**Answer:**

* **Covering Index:** Includes all columns needed for a query, so the query can be answered entirely from the index.

```sql
CREATE INDEX idx_orders_covering ON Orders(customer_id) INCLUDE (order_date, total_amount);
```

* **Filtered Index:** Index only on subset of data.

```sql
CREATE INDEX idx_active_users ON Users(last_login) WHERE status = 'active';
```

* **Index Maintenance:**

  * Rebuild or reorganize fragmented indexes periodically.
  * Monitor index usage — drop unused indexes.
  * Avoid over-indexing (slows writes).

**Best practice:** Automate index health monitoring in large databases.

---

## F. Additional / 2025 Trends

---

### **62. How do you query and manipulate JSON or nested data structures in modern SQL engines (e.g., BigQuery, PostgreSQL, Snowflake)?**

**Answer:**
Modern SQL engines natively support JSON and nested data with special operators and functions.

* **PostgreSQL:**

  * `->` extracts JSON object.
  * `->>` extracts as text.

  ```sql
  SELECT data->>'name' AS username
  FROM Events
  WHERE data->'location'->>'country' = 'US';
  ```

  * Supports **GIN indexes** on JSONB for fast lookups.

* **BigQuery:**

  * Supports nested/repeated fields.
  * Use `JSON_EXTRACT` and `JSON_VALUE`.

  ```sql
  SELECT JSON_VALUE(payload, '$.user.name') AS username
  FROM Events
  WHERE JSON_VALUE(payload, '$.location.country') = 'US';
  ```

* **Snowflake:**

  * Stores JSON in `VARIANT` type.
  * Access fields with colon `:` operator.

  ```sql
  SELECT data:name::string AS username
  FROM Events
  WHERE data:location.country = 'US';
  ```

**Best practice:** If certain JSON fields are queried often, consider flattening them into relational columns for indexing.

---

### **63. How do you implement and version change data capture (CDC) mechanisms using SQL?**

**Answer:**
**CDC** tracks changes (inserts, updates, deletes) for replication or streaming pipelines.

**Methods:**

1. **Database-native CDC:**

   * SQL Server: `CHANGE_TRACKING`, `CHANGE_DATA_CAPTURE`.
   * Postgres: Logical replication slots (Debezium, WAL).

2. **Custom CDC with SQL:**

   * Add `last_updated_at` column.
   * Track changes using triggers:

   ```sql
   CREATE TRIGGER track_updates
   AFTER UPDATE ON Orders
   FOR EACH ROW
   INSERT INTO Orders_CDC (order_id, old_value, new_value, updated_at)
   VALUES (OLD.id, OLD.status, NEW.status, NOW());
   ```

3. **Versioning:**

   * Store versions in a history table:

   ```sql
   CREATE TABLE Orders_History (
       order_id INT,
       status VARCHAR,
       valid_from TIMESTAMP,
       valid_to TIMESTAMP
   );
   ```

**Best practice:** For large-scale pipelines, use log-based CDC (e.g., Debezium → Kafka → SQL warehouse).

---

### **64. What are the best practices for designing metrics and aggregates in streaming SQL pipelines?**

**Answer:**

* **Use time windows:** Tumbling, sliding, session windows.

  ```sql
  SELECT user_id, COUNT(*) 
  FROM ClickStream
  GROUP BY SESSION(event_time, INTERVAL '30 minutes');
  ```

* **Watermarks:** Handle late-arriving data.

* **Idempotent aggregations:** Avoid double counting when reprocessing.

* **Incremental materialization:** Continuously update aggregates in stateful stores.

* **Pre-compute high-demand metrics:** (e.g., hourly active users, rolling averages).

**Example metric:**

```sql
SELECT TUMBLE_START(event_time, INTERVAL '1 hour') AS window_start,
       COUNT(DISTINCT user_id) AS dau
FROM Events
GROUP BY TUMBLE(event_time, INTERVAL '1 hour');
```

**Best practice:** Keep metrics definitions consistent across batch and streaming (via shared SQL transformations).

---

### **65. How do you monitor SQL query performance in cloud data warehouses (e.g., query cost, latency, resource utilization)?**

**Answer:**
Cloud warehouses provide built-in query monitoring tools:

* **BigQuery:**

  * Query execution details (slots used, bytes scanned).
  * Monitor **query costs** based on scanned data.

* **Snowflake:**

  * `QUERY_HISTORY` view for runtime, scanned bytes, warehouse usage.
  * Auto-suspend/resume warehouses to control cost.

* **Redshift:**

  * `STL_QUERY` and `SVL_QLOG` system tables.

**Key metrics to track:**

* Query duration (latency).
* Bytes scanned vs table size (effectiveness of partitioning).
* Warehouse/cluster utilization (CPU, I/O).

**Best practices:**

* Use query history dashboards (e.g., Looker, Tableau).
* Identify long-tail queries and optimize with indexes/partitions.
* Apply cost alerts (BigQuery budgets, Snowflake resource monitors).

---

### **66. What techniques exist for caching query results, materializing views, and maintaining them incrementally in large-scale SQL systems?**

**Answer:**

* **Query Result Caching:**

  * BigQuery caches results for 24 hours if query is identical.
  * Snowflake caches query results and metadata.

* **Materialized Views:** Precomputed query results stored physically.

  ```sql
  CREATE MATERIALIZED VIEW daily_sales AS
  SELECT date(order_date), SUM(amount) 
  FROM Orders
  GROUP BY date(order_date);
  ```

  * Automatically refreshable.

* **Incremental Refresh:**

  * Update only new partitions instead of full recompute.
  * Example: daily partitions recomputed, past partitions left untouched.

* **External Caching:** Use Redis/Presto cache layers for hot queries.

**Best practice:** Balance freshness vs cost — use incremental refresh for large-scale aggregates.

---

### **67. How do partitioning, clustering, and bucketing strategies differ across modern cloud data warehouses (e.g., BigQuery, Redshift, Snowflake)?**

**Answer:**

* **Partitioning:**

  * Splits tables by column (usually date).
  * BigQuery: native partitioned tables.
  * Snowflake: manual partitioning via micro-partitions.
  * Redshift: uses **distribution keys** instead.

* **Clustering:**

  * Organizes data inside partitions for faster filtering.
  * BigQuery: clustering on multiple columns.
  * Snowflake: automatic clustering on frequently used columns.

* **Bucketing:**

  * Hash-based grouping of rows into buckets.
  * Redshift: **distribution style** (KEY, EVEN, ALL).
  * Hive/Spark SQL: bucketed tables for join optimization.

**Trade-offs:**

* Partitioning = best for time-series filtering.
* Clustering = improves performance on non-time queries.
* Bucketing = balances distributed joins and avoids data skew.

---

### **68. How can you design schema migrations in SQL to ensure backward compatibility and avoid downtime in production systems?**

**Answer:**
**Best practices:**

* **Expand-Contract Pattern:**

  1. **Expand:** Add new schema changes (new column, new table).
  2. Deploy application that uses both old and new.
  3. **Contract:** Remove old schema once unused.

* **Backward compatibility:**

  * Never drop or rename columns in one step.
  * Use default values for new columns.
  * Add new indexes online (Postgres `CONCURRENTLY`, MySQL `ONLINE`).

* **Zero-downtime migration techniques:**

  * Run schema migrations in transactions if supported.
  * Use **blue-green deployments** or shadow tables.
  * Data copy in background, then atomic swap (`ALTER TABLE RENAME`).

**Example (adding a new column safely):**

```sql
ALTER TABLE Orders ADD COLUMN status_new VARCHAR(20) DEFAULT 'pending';
-- Application writes to both status and status_new
-- Once all clients migrated, drop old column
```

---
---

[1]: https://pg-p.ctme.caltech.edu/blog/data-science/top-sql-interview-questions-for-data-engineers?utm_source=chatgpt.com "The Top SQL Interview Questions for Data Engineers - Caltech"
[2]: https://360digitmg.com/blog/data-engineer-sql-interview-questions?utm_source=chatgpt.com "Top 35 SQL Interview Questions for Data Engineer - 360DigiTMG"
[3]: https://www.datacamp.com/blog/top-sql-interview-questions-and-answers-for-beginners-and-intermediate-practitioners?utm_source=chatgpt.com "Top 85 SQL Interview Questions and Answers for 2025 - DataCamp"
[4]: https://www.datainterview.com/blog/top-100-sql-interview-questions?utm_source=chatgpt.com "Top 100 SQL Interview Questions in 2025 (FAANGs, Startups)"
[5]: https://www.interviewquery.com/p/data-engineer-sql-questions?utm_source=chatgpt.com "Top 12 SQL Interview Questions for Data Engineers in 2025"
[6]: https://www.vishalbarvaliya.com/most-asked-sql-interview-questions-in-data-engineering-interviews?utm_source=chatgpt.com "Most Asked SQL Interview Questions in Data Engineering Interviews"
[7]: https://bigtechinterviews.com/top-31-data-engineer-interview-questions/?utm_source=chatgpt.com "Data Engineer SQL Interview Questions - BigTechInterviews"
[8]: https://en.wikipedia.org/wiki/Hierarchical_and_recursive_queries_in_SQL?utm_source=chatgpt.com "Hierarchical and recursive queries in SQL"

---