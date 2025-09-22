Here’s a comprehensive, structured list of SQL interview questions you might see for **Data Engineer** roles — starting from foundational/basic up through advanced / optimization / design. I’ve ordered them so you can build up from basics to more complex topics. Use this as prep checklist; I can also pull up practice problems or sample answers if you want.

---

## SQL Interview Questions for Data Engineers

---

### A. Basics / Fundamentals

1. What is SQL? What is a relational database?
2. What are the different types of SQL statements / command categories (DDL, DML, DCL, TCL, etc.)? ([Caltech Bootcamps][1])
3. What are primary keys, foreign keys, unique keys? Differences? ([360digitmg.com][2])
4. What are data types (CHAR, VARCHAR, INT, DATE, etc.)? When to use which? ([DataCamp][3])
5. What is normalization? What are normal forms? Why normalize, and what are trade-offs (denormalization)? ([360digitmg.com][2])
6. What is a JOIN? What are different types (INNER, LEFT, RIGHT, FULL OUTER)? When to use which? ([Datainterview.com][4])
7. What is the difference between WHERE vs HAVING? ([Interview Query][5])
8. What is GROUP BY and ORDER BY; what are aggregations? COUNT, SUM, AVG, MIN, MAX. ([DataCamp][3])
9. Difference between UNION vs UNION ALL; INTERSECT; EXCEPT / MINUS. ([Caltech Bootcamps][1])
10. Difference between DELETE, TRUNCATE, DROP. ([DataCamp][3])
11. What are Views? When to use? Pros/cons. ([Datainterview.com][4])
12. What are stored procedures, functions, triggers? When to use? ([Datainterview.com][4])

---

### B. Intermediate / SQL Querying & Data Manipulation

13. How do you find duplicate rows in a table? And how to delete duplicates but keep one instance. ([vishalbarvaliya.com][6])
14. How to find the *nth highest salary* (e.g. 2nd highest) in a table. ([Datainterview.com][4])
15. How to get the latest record per group (e.g. latest timestamp per user). ([bigtechinterviews.com][7])
16. Use of subqueries (correlated vs non-correlated). ([Datainterview.com][4])
17. Use of Common Table Expressions (CTEs) / WITH clauses. ([Interview Query][5])
18. Window functions (ROW\_NUMBER, RANK, DENSE\_RANK, LEAD, LAG, etc.). ([Datainterview.com][4])
19. Self-joins; hierarchical queries; recursive queries. ([Wikipedia][8])
20. Pivot / Unpivot operations. ([Datainterview.com][4])
21. CASE expressions; conditional logic in SQL queries. ([DataCamp][3])
22. Use of temporary tables; derived tables; table variables. ([Datainterview.com][4])

---

### C. Advanced Topics / Performance, Design, ETL

23. Indexes: what are they, types (clustered/non-clustered), composite indexes; when/where to use; trade-offs. ([Caltech Bootcamps][1])
24. Query optimization: explain execution plan, avoiding full table scans, optimizing joins, reducing data scanned. ([Interview Query][5])
25. Partitioning (horizontal partitioning, vertical) and sharding; when useful; how to design. ([Datainterview.com][4])
26. Materialized views; indexed views. ([Datainterview.com][4])
27. Transactions; ACID properties; isolation levels; locking; concurrency issues. ([360digitmg.com][2])
28. ETL / data pipeline SQL tasks: incremental vs full load; staging tables; error handling; deduplication; data quality. ([Interview Query][5])
29. Schema design / database design: relational schemas, star vs snowflake schema; denormalization trade‐offs; surrogate vs natural keys. ([Datainterview.com][4])
30. Dealing with very large tables: how to optimize, how to scale; techniques like partition pruning, parallelism. ([Interview Query][5])
31. Handling NULLs; three-valued logic; default values; implications in joins / aggregations. ([DataCamp][3])
32. Security: SQL injection; permissions / roles; data masking etc. ([360digitmg.com][2])

---

### D. Scenario / Problem-Based / Mix & Real-World

33. Given two or more tables (e.g. user, orders, products), write a query to produce a metric such as “top 3 products by revenue per month” or “average order size per user over last 3 months.”
34. Design a database schema for clickstream / event data, and write sample queries (e.g. session duration, bounce rate etc.).
35. Given a table with events & timestamps, find gaps or detect missing data (for example: detect days when no events, or find longest streak of inactivity per user).
36. Given logs / raw data, write SQL to do data cleaning or transformation: e.g. mapping codes, splitting / parsing strings, deduplicating, joining with lookup tables.
37. ETL scenario: implement incremental load logic; identify changed rows; handle late arriving data.
38. Given performance slowness, examine the query / schema / indexes, suggest improvements. Possibly get you to read a (simplified) execution plan and pick out bottlenecks.
39. Migrations: migrating data / schema changes; how to version schemas; backward compatibility.
40. Design for scale: partitioning, archiving, compressing, summarizing large tables; deciding when to denormalize.

---

### E. Very Advanced / Senior Level

41. Distributed SQL / Big Data SQL systems: differences, considerations (e.g. in Hive, Presto, Athena, BigQuery, Spark SQL).
42. Handling semi-structured / JSON / XML / nested data in SQL; querying, indexing.
43. Dealing with time series data: windowing, retention policies, custom aggregation.
44. Working with multi-tenant databases; restrictions, isolation, data partitioning by tenant.
45. Designing schema / pipelines for real-time vs batch data; change data capture; streaming SQL (if applicable).
46. Performance under concurrency / locking / deadlocks; design for concurrent writes/reads.
47. Advanced query rewrite / materialized metrics; incremental aggregation and rollups.
48. Cost estimation in SQL engines; trade-offs between computation vs storage vs latency.

---

If you like, I can also send you a PDF of these with example solutions / help you group by “must-know vs good to know vs extra credit”. Do you want that?

[1]: https://pg-p.ctme.caltech.edu/blog/data-science/top-sql-interview-questions-for-data-engineers?utm_source=chatgpt.com "The Top SQL Interview Questions for Data Engineers - Caltech"
[2]: https://360digitmg.com/blog/data-engineer-sql-interview-questions?utm_source=chatgpt.com "Top 35 SQL Interview Questions for Data Engineer - 360DigiTMG"
[3]: https://www.datacamp.com/blog/top-sql-interview-questions-and-answers-for-beginners-and-intermediate-practitioners?utm_source=chatgpt.com "Top 85 SQL Interview Questions and Answers for 2025 - DataCamp"
[4]: https://www.datainterview.com/blog/top-100-sql-interview-questions?utm_source=chatgpt.com "Top 100 SQL Interview Questions in 2025 (FAANGs, Startups)"
[5]: https://www.interviewquery.com/p/data-engineer-sql-questions?utm_source=chatgpt.com "Top 12 SQL Interview Questions for Data Engineers in 2025"
[6]: https://www.vishalbarvaliya.com/most-asked-sql-interview-questions-in-data-engineering-interviews?utm_source=chatgpt.com "Most Asked SQL Interview Questions in Data Engineering Interviews"
[7]: https://bigtechinterviews.com/top-31-data-engineer-interview-questions/?utm_source=chatgpt.com "Data Engineer SQL Interview Questions - BigTechInterviews"
[8]: https://en.wikipedia.org/wiki/Hierarchical_and_recursive_queries_in_SQL?utm_source=chatgpt.com "Hierarchical and recursive queries in SQL"
