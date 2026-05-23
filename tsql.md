# 📘 T-SQL (SQL Server) Complete Interview & Learning Roadmap

> A comprehensive, topic-by-topic checklist for mastering T-SQL. Check off items as you progress. Each topic includes expanded subtopics, key concepts, and interview focus areas.

## 📊 Progress Tracker
| Category | Status | Notes |
|----------|--------|-------|
| Core Fundamentals | ⬜ Not Started | |
| Querying & Filtering | ⬜ Not Started | |
| Joins & Set Operations | ⬜ Not Started | |
| Aggregation & Grouping | ⬜ Not Started | |
| Subqueries & CTEs | ⬜ Not Started | |
| Window Functions | ⬜ Not Started | |
| Indexing & Query Optimization | ⬜ Not Started | |
| Transactions & Concurrency | ⬜ Not Started | |
| Stored Procedures & Functions | ⬜ Not Started | |
| Error Handling & Debugging | ⬜ Not Started | |
| Security & Permissions | ⬜ Not Started | |
| Modern SQL Server Features | ⬜ Not Started | |
| Integration with .NET | ⬜ Not Started | |
| Performance Tuning & Execution Plans | ⬜ Not Started | |
| Interview Prep & System Design | ⬜ Not Started | |

---

## 🌱 1. Core Fundamentals
- [ ] **T-SQL Syntax & Structure**
  - Statement termination: `;` (required for CTEs, MERGE, some window functions)
  - Batch separators: `GO` (client-side, not T-SQL), variable scope across batches
  - Comments: `-- single-line`, `/* multi-line */`, `/* nested */` support
  - Identifier rules: brackets `[Column Name]`, double quotes with `SET QUOTED_IDENTIFIER ON`
- [ ] **Data Types Deep Dive**
  - Numeric: `INT`, `BIGINT`, `DECIMAL(p,s)`, `FLOAT` (approximate), `MONEY` (avoid)
  - String: `CHAR(n)` (fixed), `VARCHAR(n)` (variable), `NVARCHAR(n)` (Unicode), `MAX` types
  - Date/Time: `DATE`, `TIME`, `DATETIME2` (prefer), `DATETIMEOFFSET`, `SYSDATETIME()`
  - Special: `BIT`, `UNIQUEIDENTIFIER` (GUID), `JSON` (stored as `NVARCHAR`), `XML`
  - Implicit conversion pitfalls: `VARCHAR` vs `NVARCHAR`, `DATETIME` vs `DATETIME2`
- [ ] **NULL Handling**
  - `NULL` = unknown, not zero or empty string. `NULL = NULL` → `UNKNOWN` (not TRUE)
  - `IS NULL` / `IS NOT NULL` for filtering; `COALESCE()`, `ISNULL()` for substitution
  - `ANSI_NULLS` setting impact on equality comparisons (always keep ON)
  - Three-valued logic: `TRUE` / `FALSE` / `UNKNOWN` in `WHERE` and `JOIN` conditions
- [ ] **Basic SELECT Patterns**
  - Column aliases: `SELECT FirstName AS FName`, `SELECT FName = FirstName`
  - `SELECT *` anti-pattern: explicit columns for performance, maintainability, API contracts
  - `TOP` with `ORDER BY`: deterministic results require unique sort keys or `WITH TIES`
  - `DISTINCT` vs `GROUP BY`: when to use each, performance implications

---

## 🔍 2. Querying & Filtering
- [ ] **WHERE Clause Mastery**
  - Comparison operators: `=`, `<>`, `>`, `<`, `>=`, `<=`, `!>` (non-standard, avoid)
  - Logical operators: `AND`, `OR`, `NOT`, precedence rules, parentheses for clarity
  - Pattern matching: `LIKE '%pattern%'`, `[a-c]` ranges, escape characters with `ESCAPE`
  - Range checks: `BETWEEN` (inclusive), `IN` (list or subquery), `EXISTS` (correlated)
- [ ] **String & Date Functions**
  - String: `CONCAT()`, `CONCAT_WS()`, `SUBSTRING()`, `LEFT/RIGHT`, `REPLACE()`, `TRIM()`
  - Date: `DATEADD()`, `DATEDIFF()`, `DATENAME()`, `DATEPART()`, `EOMONTH()`, `SYSDATETIMEOFFSET()`
  - Conversion: `CAST()`, `CONVERT(style)`, `TRY_CAST()`, `TRY_CONVERT()` (safe, returns NULL on failure)
  - Formatting: `FORMAT()` (slow, use for UI only), client-side formatting preferred
- [ ] **Advanced Filtering Patterns**
  - SARGable predicates: avoid functions on indexed columns (`WHERE YEAR(OrderDate) = 2024` → non-SARGable)
  - Parameter sniffing awareness: `OPTION (RECOMPILE)`, `OPTIMIZE FOR UNKNOWN`, local variable trick
  - Dynamic SQL safety: `sp_executesql` with parameters, never concatenate user input directly
  - Full-text search basics: `CONTAINS()`, `FREETEXT()`, full-text indexes, stoplists

---

## 🔗 3. Joins & Set Operations
- [ ] **JOIN Types & Semantics**
  - `INNER JOIN`: matching rows only
  - `LEFT/RIGHT OUTER JOIN`: preserve left/right table rows, `NULL` for non-matches
  - `FULL OUTER JOIN`: preserve both sides, `NULL` where no match
  - `CROSS JOIN`: Cartesian product (use intentionally, e.g., date dimension generation)
- [ ] **JOIN Performance & Pitfalls**
  - Join order: optimizer usually handles, but complex queries may benefit from hints (`OPTION (FORCE ORDER)`)
  - Missing join conditions: accidental Cartesian products, `WHERE` vs `ON` placement for outer joins
  - Composite keys: all key columns must be in `ON` clause for correct semantics
  - `EXISTS` vs `IN` vs `JOIN` for existence checks: `EXISTS` often more efficient with correlated subqueries
- [ ] **Set Operations**
  - `UNION` (distinct) vs `UNION ALL` (preserve duplicates, faster)
  - `INTERSECT`: rows present in both queries
  - `EXCEPT`: rows in first query not in second
  - Requirements: same number of columns, compatible data types, column names from first query
- [ ] **Advanced Join Patterns**
  - Self-joins: hierarchical data (employees/managers), comparing rows within same table
  - Non-equi joins: `ON a.StartDate <= b.EndDate AND a.EndDate >= b.StartDate` (temporal overlaps)
  - Lateral joins: `CROSS APPLY` / `OUTER APPLY` for table-valued functions, correlated subqueries as tables

---

## 📊 4. Aggregation & Grouping
- [ ] **Aggregate Functions**
  - `COUNT(*)` vs `COUNT(column)` vs `COUNT(DISTINCT column)`: NULL handling differences
  - `SUM()`, `AVG()`, `MIN()`, `MAX()`: ignore NULLs by default, `COALESCE` for zero defaults
  - `STRING_AGG(column, separator) WITHIN GROUP (ORDER BY ...)`: concatenation with ordering
  - `CHECKSUM_AGG()`, `GROUPING_ID()`: advanced aggregation metadata
- [ ] **GROUP BY Mastery**
  - Single/multi-column grouping, grouping sets: `GROUP BY GROUPING SETS ((a,b), (a), ())`
  - `ROLLUP` (hierarchical subtotals) vs `CUBE` (all combinations) vs `GROUPING SETS` (explicit)
  - `HAVING` clause: filter aggregated results (post-aggregation), vs `WHERE` (pre-aggregation)
  - `GROUP BY` with non-aggregated columns: all non-aggregated SELECT columns must be in GROUP BY
- [ ] **Pivoting & Unpivoting**
  - `PIVOT`: rotate rows to columns (e.g., months as columns), requires aggregation
  - `UNPIVOT`: rotate columns to rows (normalize wide tables)
  - Dynamic pivoting: build column list with `FOR XML PATH`, execute via `sp_executesql`
  - When to pivot in SQL vs application layer: complexity, maintainability, client flexibility

---

## 🔄 5. Subqueries & Common Table Expressions (CTEs)
- [ ] **Subquery Types**
  - Scalar subquery: returns single value, usable in SELECT/WHERE
  - Row subquery: returns single row, usable with `=`, `IN`, `EXISTS`
  - Table subquery: returns result set, usable in `FROM` (derived table), `JOIN`, `IN`
  - Correlated subquery: references outer query columns, executes per outer row (performance caution)
- [ ] **Common Table Expressions (CTEs)**
  - Syntax: `WITH CTE_Name AS (SELECT ...) SELECT * FROM CTE_Name`
  - Benefits: readability, recursion, modular query building, multiple references without duplication
  - Scope: CTE exists only for the immediately following statement
  - Multiple CTEs: comma-separated, can reference prior CTEs in same `WITH` clause
- [ ] **Recursive CTEs**
  - Structure: anchor member `UNION ALL` recursive member, termination condition
  - Use cases: hierarchical data (org charts, categories), graph traversal, sequence generation
  - `MAXRECURSION` hint: prevent infinite loops (default 100, 0 = unlimited, use cautiously)
  - Performance: can be expensive on deep hierarchies; consider closure tables or nested sets for frequent access
- [ ] **Derived Tables vs CTEs vs Temp Tables**
  - Derived table: inline subquery in `FROM`, scoped to single query, no indexing
  - CTE: named, reusable within query, no statistics, no indexing
  - Temp table (`#Temp`): physical tempdb object, supports indexes/statistics, persists across statements in session
  - Table variable (`@Table`): memory-optimized (usually), no statistics (pre-SQL 2019), limited scope

---

## 🪟 6. Window Functions (Advanced Analytics)
- [ ] **Window Function Fundamentals**
  - Syntax: `FUNCTION() OVER (PARTITION BY ... ORDER BY ... ROWS/RANGE ...)`
  - `PARTITION BY`: divides result set into groups (like `GROUP BY` but retains row detail)
  - `ORDER BY` within `OVER`: defines window frame ordering, required for ranking/analytic functions
  - Frame specification: `ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW` (default for aggregates)
- [ ] **Ranking Functions**
  - `ROW_NUMBER()`: unique sequential integer, resets per partition, no ties handling
  - `RANK()`: same rank for ties, skips next rank (1,2,2,4)
  - `DENSE_RANK()`: same rank for ties, no gaps (1,2,2,3)
  - `NTILE(n)`: distributes rows into n approximately equal buckets
- [ ] **Value & Analytic Functions**
  - `LAG(column, offset, default)`: access prior row value within partition
  - `LEAD(column, offset, default)`: access next row value within partition
  - `FIRST_VALUE()`, `LAST_VALUE()`: first/last value in window frame (watch frame boundaries)
  - `SUM() OVER (...)`, `AVG() OVER (...)`: running totals, moving averages
- [ ] **Frame Specification Mastery**
  - `ROWS` vs `RANGE`: `ROWS` is physical row count, `RANGE` is logical value range (handles ties differently)
  - Common frames: 
    - Running total: `ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW`
    - Moving average (3 rows): `ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING`
    - Cumulative from start: default frame
  - `EXCLUDE` clause (SQL Server 2022+): `EXCLUDE CURRENT ROW`, `EXCLUDE GROUP`, etc.

---

## ⚡ 7. Indexing & Query Optimization
- [ ] **Index Types Deep Dive**
  - Clustered index: physical row order, one per table, typically on PK (range queries, `ORDER BY`)
  - Non-clustered index: separate structure with key + bookmark (RID/Clustered Key), multiple allowed
  - Covering index: includes all columns needed by query (`INCLUDE` clause), avoids key lookup
  - Filtered index: `WHERE IsActive = 1`, smaller, more selective, maintenance efficient
  - Columnstore index: batch mode processing, compression, ideal for analytics/large scans
- [ ] **Index Design Principles**
  - Selectivity: high selectivity (many distinct values) → better index performance
  - Leftmost prefix: composite index `(LastName, FirstName)` supports `WHERE LastName = 'X'` but not `FirstName = 'Y'` alone
  - Key order: put equality predicates first, then range, then `ORDER BY` columns
  - Include vs Key columns: `INCLUDE` adds non-key columns to leaf level, doesn't affect seek ability
- [ ] **Execution Plan Analysis**
  - Read left-to-right, top-to-bottom: data flow, not execution order
  - Key operators: `Index Seek` (good), `Index Scan` (caution), `Key Lookup` (expensive), `Sort` (memory grant)
  - Cost percentages: relative within plan, not absolute; focus on high-cost operators
  - Actual vs Estimated rows: large discrepancies indicate outdated statistics or parameter sniffing
- [ ] **Statistics & Maintenance**
  - Statistics: histograms on index/key columns, used by optimizer for cardinality estimates
  - Update statistics: `UPDATE STATISTICS`, `sp_updatestats`, auto-update thresholds
  - Index fragmentation: `sys.dm_db_index_physical_stats`, `ALTER INDEX ... REORGANIZE/REBUILD`
  - Maintenance strategy: Ola Hallengren scripts, off-peak scheduling, fill factor considerations

---

## 🔐 8. Transactions & Concurrency Control
- [ ] **ACID Properties & Transaction Basics**
  - Atomicity: all-or-nothing, `BEGIN TRAN` / `COMMIT` / `ROLLBACK`
  - Consistency: constraints, triggers, business rules enforce valid state transitions
  - Isolation: transaction visibility to others, controlled by isolation levels
  - Durability: committed data survives crashes, write-ahead logging (WAL)
- [ ] **Isolation Levels Deep Dive**
  - `READ UNCOMMITTED`: dirty reads, no shared locks, highest concurrency, lowest consistency
  - `READ COMMITTED` (default): no dirty reads, shared locks released after read, non-repeatable reads possible
  - `REPEATABLE READ`: shared locks held until end of transaction, prevents non-repeatable reads, phantom reads possible
  - `SERIALIZABLE`: range locks, prevents phantoms, highest consistency, lowest concurrency
  - `SNAPSHOT`: row versioning in tempdb, no blocking readers/writers, requires `ALLOW_SNAPSHOT_ISOLATION ON`
- [ ] **Locking & Blocking**
  - Lock types: Shared (S), Update (U), Exclusive (X), Intent (IS, IX, SIX), Schema (Sch-M, Sch-S)
  - Lock escalation: many row locks → table lock to reduce memory pressure, `ALTER TABLE ... SET (LOCK_ESCALATION = ...)`
  - Blocking vs deadlocks: blocking is waiting, deadlock is cyclic dependency (victim chosen, error 1205)
  - Diagnosis: `sp_who2`, `sys.dm_exec_requests`, `sys.dm_tran_locks`, Extended Events, SQL Profiler (deprecated)
- [ ] **Deadlock Prevention Strategies**
  - Access objects in consistent order across transactions
  - Keep transactions short, acquire locks late, release early
  - Use `WITH (NOLOCK)` cautiously (dirty reads) or `READ COMMITTED SNAPSHOT` for non-blocking reads
  - Retry logic in application: catch error 1205, retry with exponential backoff
- [ ] **Explicit Transaction Patterns**
  - `SET XACT_ABORT ON`: auto-rollback on runtime errors (recommended for data-modifying procs)
  - Savepoints: `SAVE TRAN name`, `ROLLBACK TRAN name` for partial rollback
  - Nested transactions: `@@TRANCOUNT` tracking, only outermost `COMMIT` persists, any `ROLLBACK` rolls back all

---

## ⚙️ 9. Stored Procedures, Functions & Triggers
- [ ] **Stored Procedures**
  - Creation: `CREATE PROCEDURE dbo.usp_GetOrders @CustomerId INT AS BEGIN ... END`
  - Parameters: input (`@Param INT`), output (`@Result INT OUTPUT`), default values (`@Status BIT = 1`)
  - Execution: `EXEC dbo.usp_GetOrders @CustomerId = 123`, capture output params, return codes
  - Benefits: precompiled execution plan, reduced network traffic, encapsulation, security boundary
- [ ] **User-Defined Functions (UDFs)**
  - Scalar UDFs: return single value, can be used in SELECT/WHERE, but can cause row-by-row performance issues
  - Inline Table-Valued Functions (iTVF): `RETURNS TABLE RETURN (SELECT ...)`, optimized like views, preferred
  - Multi-Statement TVFs: `RETURNS @Table TABLE (...) BEGIN ... RETURN END`, can have logic but less efficient
  - Deterministic vs non-deterministic: impacts indexing, replication, computed columns
- [ ] **Triggers**
  - DML triggers: `AFTER INSERT/UPDATE/DELETE`, `INSTEAD OF` (for views/complex logic)
  - `inserted` / `deleted` pseudo-tables: access changed rows, handle multi-row operations
  - Best practices: keep triggers short, avoid business logic, document side effects, test for recursion
  - Alternatives: change data capture (CDC), temporal tables, application-layer event handling
- [ ] **Modular Code Patterns**
  - Error handling in procs: `TRY...CATCH`, `THROW`, logging to audit table
  - Dynamic SQL in procs: `sp_executesql` with parameters, validate inputs, avoid SQL injection
  - Return patterns: result sets, output parameters, return codes, table-valued parameters (TVPs) for batch operations

---

## 🛡️ 10. Error Handling & Debugging
- [ ] **Structured Error Handling**
  - `TRY...CATCH` blocks: capture `ERROR_NUMBER()`, `ERROR_MESSAGE()`, `ERROR_SEVERITY()`, `ERROR_STATE()`
  - `THROW` vs `RAISERROR`: `THROW` re-throws current error or raises new (SQL 2012+), preferred
  - Transaction management in CATCH: `IF @@TRANCOUNT > 0 ROLLBACK`, avoid uncommittable transactions
  - Custom error messages: `sp_addmessage`, localization, severity levels (user vs system)
- [ ] **Debugging Techniques**
  - `PRINT` vs `SELECT` for output: `PRINT` to messages tab, `SELECT` as result set
  - `RAISERROR(... WITH NOWAIT)`: immediate message flush during long operations
  - SQL Server Management Studio (SSMS): breakpoints, watch window, local variables in debug mode
  - Extended Events: lightweight tracing, capture query execution, errors, performance metrics
- [ ] **Logging & Auditing Patterns**
  - Centralized error log table: `ErrorId`, `ProcedureName`, `ErrorMessage`, `StackTrace`, `Timestamp`, `UserId`
  - Application-layer logging correlation: pass `@CorrelationId` from .NET to SQL for end-to-end tracing
  - Change tracking: `CHANGE_TRACKING` feature vs manual audit tables vs temporal tables
  - Compliance considerations: GDPR, HIPAA, data retention policies, encryption at rest/in transit

---

## 🔐 11. Security & Permissions
- [ ] **Authentication & Authorization**
  - Windows Authentication vs SQL Authentication: integrated security preferred, avoid SQL auth in prod
  - Logins (server-level) vs Users (database-level): `CREATE LOGIN`, `CREATE USER`, mapping
  - Roles: fixed server roles (`sysadmin`), fixed database roles (`db_owner`), custom database roles
  - Principle of least privilege: grant only necessary permissions, avoid `db_owner` for app accounts
- [ ] **Permission Management**
  - GRANT / DENY / REVOKE: object-level (`GRANT SELECT ON dbo.Orders TO AppUser`), schema-level, database-level
  - Effective permissions: `fn_my_permissions()`, `HAS_PERMS_BY_NAME()`, role membership inheritance
  - Schema ownership: separate schemas for security boundaries (`Security.SensitiveData`), `EXECUTE AS`
  - Row-Level Security (RLS): predicate functions, `FILTER PREDICATE`, `BLOCK PREDICATE` for multi-tenant apps
- [ ] **Data Protection**
  - Encryption: Transparent Data Encryption (TDE) for at-rest, Always Encrypted for client-side column encryption
  - Dynamic Data Masking: `MASKED WITH (FUNCTION = 'partial(...)')` for dev/test, not security boundary
  - SQL Injection Prevention: parameterized queries (`sp_executesql`), ORM (EF Core/Dapper) best practices
  - Auditing: SQL Audit feature, track SELECT/INSERT/UPDATE/DELETE on sensitive objects, compliance reporting

---

## 🆕 12. Modern SQL Server Features
- [ ] **JSON Support**
  - `FOR JSON PATH/AUTO`: convert relational results to JSON
  - `OPENJSON()`: parse JSON into relational rows, schema definition with `WITH` clause
  - `ISJSON()`, `JSON_VALUE()`, `JSON_QUERY()`, `JSON_MODIFY()`: validation, extraction, mutation
  - Use cases: flexible schemas, API payloads, hybrid relational/document storage
- [ ] **Temporal Tables**
  - System-versioned tables: `PERIOD FOR SYSTEM_TIME`, automatic history tracking in separate table
  - Querying history: `FOR SYSTEM_TIME AS OF`, `BETWEEN`, `CONTAINED IN`, `ALL`
  - Use cases: audit trails, point-in-time recovery, trend analysis without custom triggers
  - Limitations: schema change complexity, storage growth, performance considerations
- [ ] **Graph Database Features**
  - Node tables: `CREATE TABLE Person AS NODE`, edge tables: `CREATE TABLE Friends AS EDGE`
  - Pattern matching: `MATCH(SHORTEST_PATH(...))`, graph traversal queries
  - Use cases: social networks, recommendation engines, organizational hierarchies
  - Integration: combine with relational queries, `SHORTEST_PATH` for analytics
- [ ] **Intelligent Query Processing (IQP)**
  - Batch mode on rowstore: columnstore-like performance for analytical queries on rowstore tables
  - Memory grant feedback: auto-corrects under/over-estimated memory grants across executions
  - Adaptive joins: switches between hash/loop join at runtime based on actual row counts
  - Scalar UDF inlining: transforms scalar UDFs into relational expressions for better optimization

---

## 🔗 13. Integration with .NET (ASP.NET Core)
- [ ] **Connection Management**
  - Connection strings: `Server=...;Database=...;User Id=...;Password=...;Encrypt=True;TrustServerCertificate=False`
  - Connection pooling: default enabled, `Max Pool Size`, `Min Pool Size`, `Connection Lifetime`
  - Async ADO.NET: `SqlConnection.OpenAsync()`, `SqlCommand.ExecuteReaderAsync()`, `CancellationToken`
  - Resiliency: Polly retry policies for transient errors (SQL error numbers: -1, 40613, 40197, 40501)
- [ ] **EF Core Integration**
  - DbContext configuration: `options.UseSqlServer(connectionString, sqlOptions => sqlOptions.EnableRetryOnFailure())`
  - Migrations: `Add-Migration`, `Update-Database`, `Script-Migration` for production deployments
  - LINQ to Entities: translation to T-SQL, avoiding client evaluation (`.AsEnumerable()` pitfalls)
  - Performance: `AsNoTracking()` for read-only, explicit loading vs eager loading (`Include`), split queries
- [ ] **Dapper Integration**
  - Micro-ORM advantages: raw SQL control, minimal abstraction, high performance
  - Parameterization: `connection.Query<T>("SELECT * FROM Users WHERE Id = @Id", new { Id = 123 })`
  - Multi-mapping: `Query<TFirst, TSecond, TReturn>(..., splitOn: "Id")` for joins
  - Bulk operations: `SqlBulkCopy` integration, `Dapper.Bulk` extensions, table-valued parameters
- [ ] **Data Access Patterns**
  - Repository pattern: abstraction over data access, testability, but avoid over-abstraction of EF Core
  - Unit of Work: `DbContext` as UoW, `SaveChangesAsync()` as commit, transaction scope coordination
  - CQRS: separate read/write models, Dapper for complex reads, EF Core for writes
  - API contract alignment: return DTOs matching React frontend expectations, avoid over-fetching

---

## 🚀 14. Performance Tuning & Execution Plans
- [ ] **Query Tuning Methodology**
  - Identify: slow queries via Query Store, Extended Events, `sys.dm_exec_query_stats`
  - Analyze: actual execution plan, statistics IO/TIME, missing index requests
  - Hypothesize: missing index, outdated stats, parameter sniffing, implicit conversion
  - Test: `OPTION (RECOMPILE)`, index hints (last resort), query rewrite, statistics update
  - Validate: measure before/after with consistent workload, monitor in production
- [ ] **Common Performance Anti-Patterns**
  - `SELECT *`: unnecessary I/O, network traffic, breaks covering indexes
  - Functions on indexed columns in WHERE: `WHERE YEAR(OrderDate) = 2024` → index scan
  - Implicit conversions: `VARCHAR` column compared to `NVARCHAR` parameter → index scan
  - Cursors: row-by-row processing, replace with set-based operations when possible
  - Over-indexing: write overhead, maintenance cost, choose indexes based on query patterns
- [ ] **Advanced Tuning Techniques**
  - Query hints: `OPTION (RECOMPILE)`, `OPTIMIZE FOR (@Param = VALUE)`, `USE HINT('ENABLE_PARALLEL_PLAN_PREFERENCE')`
  - Plan guides: force specific plan for problematic queries without code change
  - In-Memory OLTP: memory-optimized tables, natively compiled stored procedures for extreme throughput
  - Partitioning: large table management, partition elimination for query performance, maintenance efficiency
- [ ] **Monitoring & Alerting**
  - Query Store: force plans, track regressions, identify top resource consumers
  - DMVs: `sys.dm_exec_requests`, `sys.dm_os_wait_stats`, `sys.dm_db_index_usage_stats`
  - Alerts: SQL Agent alerts for severity 16-25 errors, deadlocks, long-running queries
  - Baseline metrics: establish normal performance, detect anomalies proactively

---

## 🎯 15. Interview Prep & System Design
- [ ] **Coding Interview Drills**
  - Write a query to find the Nth highest salary without `TOP`/`LIMIT` (use `DENSE_RANK`)
  - Calculate running totals, moving averages using window functions
  - Recursive CTE: generate date range, traverse employee hierarchy
  - Pivot monthly sales data: rows to columns transformation
  - Identify gaps and islands in sequential data (e.g., missing order numbers)
- [ ] **System Design Scenarios**
  - Design a multi-tenant SaaS database: schema-per-tenant vs shared schema with `TenantId`, RLS, isolation
  - High-traffic e-commerce: read replicas, caching strategy (Redis), eventual consistency for inventory
  - Real-time analytics dashboard: columnstore indexes, materialized views, incremental aggregation
  - Audit/compliance requirements: temporal tables vs CDC vs custom audit triggers, retention policies
- [ ] **Behavioral & Architecture Questions**
  - "How do you approach tuning a slow-running query?" (methodology, tools, collaboration)
  - "When would you choose a stored procedure vs application-layer logic?" (security, performance, maintainability)
  - "How do you handle database schema changes in production?" (migrations, backward compatibility, rollback)
  - "Describe a time you resolved a production deadlock." (diagnosis, root cause, prevention)
- [ ] **Mock Interview Questions**
  - *Explain the difference between `DELETE`, `TRUNCATE`, and `DROP`.*
  - *How does `READ COMMITTED SNAPSHOT` isolation work, and when would you enable it?*
  - *Write a query to find customers who placed orders in both January and February.*
  - *How would you design a reporting table that aggregates daily sales from a high-volume orders table?*
  - *What are the tradeoffs between EF Core and Dapper for a new .NET API project?*
- [ ] **Code Review Checklist**
  - Security: parameterized queries, least-privilege permissions, no dynamic SQL concatenation
  - Performance: SARGable predicates, appropriate indexes, avoid `SELECT *`, check execution plans
  - Maintainability: clear aliases, comments for complex logic, consistent formatting, error handling
  - Correctness: NULL handling, JOIN conditions, GROUP BY completeness, transaction scope

---

## 📌 How to Use This Checklist
1. **Track Progress**: Replace `⬜ Not Started` in the tracker with `✅ Done` as you complete sections.
2. **Learn in Order**: Follow the sequence. Later topics build on earlier foundations.
3. **Practice Queries**: Every concept should be implemented in SQL Server Management Studio (SSMS) or Azure Data Studio. Use the [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sample database for realistic practice.
4. **Interview Prep**: Use the expanded subtopics to generate flashcards. Practice explaining each out loud in <60 seconds. Write queries from memory.
5. **Stay Updated**: SQL Server evolves. Bookmark the [SQL Server Blog](https://cloudblogs.microsoft.com/sqlserver/) and [Microsoft Learn T-SQL Docs](https://learn.microsoft.com/sql/t-sql/) for new features.

> 💡 *Tip: Don't just memorize syntax. Build a small full-stack app (React + ASP.NET Core API + SQL Server) using at least 3 patterns from this list. Real implementation beats theoretical knowledge in interviews.*

> 🔗 *Cross-Stack Bonus*: When studying ASP.NET Core, implement the API layer that executes your T-SQL queries. When studying React, design the frontend that consumes the API responses shaped by your T-SQL. Full-stack context makes you 10x more valuable.

> 🛠 *Tooling Recommendation*: Use Azure Data Studio (free, cross-platform) with the `kexec` extension for executing queries, `query-history` for tracking, and `execution-plan` for visualizing plans. Pair with `dbatools` PowerShell module for automation.
