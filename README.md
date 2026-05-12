
🧭 Quick Navigation (Click to Jump)
<details open>
<summary><strong>🔹 .NET Ecosystem</strong></summary>

C# Fundamentals
Object-Oriented Programming
Advanced C#
ASP.NET Core
Web API
Entity Framework Core
SQL Server
Design Patterns
Microservices
Cloud & DevOps
Testing
Security
Performance Optimization
Architecture & Best Practices
Real-Time & Messaging
</details>

<details>
<summary><strong>🔹 React JS</strong></summary>

React Fundamentals
React Hooks
Component Lifecycle
State Management
React Routing
API Integration
Performance Optimization
Advanced React Concepts
Forms & Validation
Authentication & Security
Styling in React
TypeScript with React
React Testing
Build & Deployment
React Architecture
Real-Time Features
React + Backend Integration
</details>

<details>
<summary><strong>🔹 SQL Mastery</strong></summary>

SQL Fundamentals
Database Design
CRUD Operations
SQL Queries
Joins
Functions
Subqueries
Views
Stored Procedures
Triggers
Indexes
Transactions
Locks & Concurrency
Common Table Expressions
Temporary Objects
Advanced SQL Concepts
Performance Optimization
Security
Backup & Recovery
SQL Server Architecture
ETL & Data Handling
</details>

🔹 .NET ECOSYSTEM
<a id="c-fundamentals"></a>1. C# Fundamentals
<details>
<summary>▶️ Expand Topics</summary>

Core Concepts
Data Types: int, string, bool, decimal, DateTime, etc.
Value Type vs Reference Type: Stack vs Heap memory allocation
Boxing and Unboxing: Converting value types to object and back
Nullable Types: int?, Nullable<T>, null-coalescing operators (??, ?.)
Type Casting: Implicit, explicit, as, is, Convert class
var vs dynamic vs object: Compile-time vs runtime typing
String vs StringBuilder: Immutability and performance implications
Collections & Data Structures
Arrays and Collections: Array, List<T>, Dictionary<TKey,TValue>, HashSet<T>
Generics: Type safety, List<T>, generic methods/classes
Tuples: ValueTuple, named tuples, deconstruction
Anonymous Types: Inline object creation with var
Advanced Language Features
Exception Handling: try-catch-finally, custom exceptions, exception filters
Delegates & Events: Action, Func, event keyword, publisher-subscriber pattern
Lambda Expressions: => syntax, expression vs statement lambdas
Extension Methods: Adding methods to existing types without inheritance
LINQ: Query syntax vs method syntax, IEnumerable vs IQueryable
Async and Await: Task, Task<T>, asynchronous programming patterns
Reflection & Attributes: Runtime type inspection, custom attributes
Memory & DI
Garbage Collection: Generations, finalizers, GC.Collect()
IDisposable and using: Resource management, using statements
Dependency Injection Basics: Constructor injection, service lifetimes (Transient, Scoped, Singleton)
</details>

<a id="oop"></a>2. Object-Oriented Programming (OOP)
<details>
<summary>▶️ Expand Topics</summary>

Four Pillars
Encapsulation: Access modifiers (private, public, protected, internal)
Abstraction: Abstract classes, interfaces, hiding implementation details
Inheritance: Base/derived classes, base keyword, method inheritance
Polymorphism: Compile-time (overloading) vs runtime (overriding)
Key Concepts
Method Overloading: Same name, different parameters
Method Overriding: virtual, override, new keywords
Abstract Class vs Interface: When to use which, multiple interface implementation
Sealed Class: Preventing inheritance
Static Class: Non-instantiable, static members only
Design Principles
SOLID Principles:
Single Responsibility
Open/Closed
Liskov Substitution
Interface Segregation
Dependency Inversion
</details>

<a id="advanced-c"></a>3. Advanced C#
<details>
<summary>▶️ Expand Topics</summary>

Concurrency & Parallelism
Task Parallel Library (TPL): Task.Run, Parallel.For, Parallel.ForEach
Multithreading: Thread class, thread pool, background workers
Thread vs Task: When to use which abstraction
Synchronization: lock, Monitor, Mutex, Semaphore, SemaphoreSlim
Deadlocks: Causes, detection, prevention strategies
Advanced Type System
Covariance and Contravariance: in and out keywords with generics
Memory Management: Span<T>, Memory<T>, stack-allocated memory
Records: Immutable reference types, value-based equality
Pattern Matching: is expressions, switch expressions, property patterns
Expression Trees: Expression<Func<T>>, dynamic query building
</details>

<a id="aspnet-core"></a>4. ASP.NET Core
<details>
<summary>▶️ Expand Topics</summary>

Architecture & Pipeline
ASP.NET Core Architecture: Startup.cs, Program.cs, host builder
Middleware: Request pipeline, custom middleware, order matters
Dependency Injection: Built-in container, service registration
Routing: Attribute routing, conventional routing, route constraints
Request Handling
Model Binding: From query, route, body, form
Filters: Authorization, resource, action, exception, result filters
Controllers and Actions: Return types (IActionResult, ActionResult<T>)
Minimal APIs: Lightweight endpoint definition without controllers
Configuration & Observability
Configuration: appsettings.json, environment-specific configs, user secrets
Environment Variables: IWebHostEnvironment, ASPNETCORE_ENVIRONMENT
Logging: ILogger, structured logging, providers (Console, Debug, File)
Exception Middleware: Global error handling, problem details
Security & State
Authentication: Cookie, JWT, OAuth, OpenID Connect
Authorization: Policies, roles, claims-based authorization
JWT Authentication: Token generation, validation, refresh flow
Identity Framework: User management, roles, claims, password hashing
Session Management: In-memory, distributed sessions
Caching: In-memory, distributed caching with Redis
Advanced Features
SignalR: Real-time communication, hubs, clients
Background Services: IHostedService, BackgroundService
API Versioning: URL, query string, header versioning strategies
</details>

<a id="web-api"></a>5. Web API
<details>
<summary>▶️ Expand Topics</summary>

REST Fundamentals
REST API Principles: Stateless, resource-based, uniform interface
HTTP Methods: GET, POST, PUT, PATCH, DELETE
Status Codes: 200, 201, 400, 401, 403, 404, 500
CRUD Operations: Mapping HTTP verbs to database operations
Documentation & Testing
Swagger / OpenAPI: Auto-generated docs, XML comments, custom UI
Postman Testing: Collections, environments, automated tests
Security & Reliability
API Security: HTTPS, input validation, output encoding
JWT Tokens: Structure, signing, validation, expiration
OAuth Basics: Flows (authorization code, client credentials), scopes
API Validation: FluentValidation, data annotations, custom validators
Global Exception Handling: Middleware, problem details RFC 7807
Scalability Features
Pagination: Offset-based, cursor-based, metadata responses
Rate Limiting: Fixed window, sliding window, token bucket
File Upload APIs: IFormFile, streaming, size limits, validation
</details>

<a id="ef-core"></a>6. Entity Framework Core
<details>
<summary>▶️ Expand Topics</summary>

Core Concepts
DbContext: Unit of Work pattern, change tracking, SaveChanges()
Code First Approach: POCO entities, migrations, model configuration
Database First: Scaffolding from existing database
Migrations: Add, update, script, rollback
Data Loading Strategies
LINQ Queries: Method vs query syntax, projection, filtering
Lazy Loading: Proxy generation, navigation properties
Eager Loading: .Include(), .ThenInclude()
Explicit Loading: Entry().Collection().Load()
Performance & Patterns
Tracking vs No Tracking: AsNoTracking() for read-only queries
Repository Pattern: Abstraction over data access
Unit of Work: Coordinating multiple repositories
Stored Procedures: Raw SQL execution, FromSqlRaw
Transactions: Database.BeginTransaction(), ambient transactions
Performance Optimization: Split queries, batching, compiled queries
</details>

<a id="sql-server-dotnet"></a>7. SQL Server
<details>
<summary>▶️ Expand Topics</summary>

Query Fundamentals
Joins: INNER, LEFT, RIGHT, FULL, CROSS, SELF
Indexes: Clustered vs non-clustered, covering indexes, index tuning
Stored Procedures: Parameters, error handling, execution plans
Views: Simple, complex, indexed views
Functions: Scalar, table-valued, built-in functions
Triggers: AFTER, INSTEAD OF, use cases and cautions
Data Integrity & Design
Transactions: BEGIN, COMMIT, ROLLBACK, savepoints
Normalization: 1NF, 2NF, 3NF, BCNF, denormalization trade-offs
Primary and Foreign Keys: Referential integrity, cascading actions
Clustered vs Non-Clustered Index: Physical storage implications
Advanced Querying
CTE: Common Table Expressions, recursive CTEs
Temp Tables: #temp, ##global, table variables
SQL Optimization: Execution plans, statistics, query hints
Execution Plans: Reading, interpreting, optimizing
</details>

<a id="design-patterns"></a>8. Design Patterns
<details>
<summary>▶️ Expand Topics</summary>

Creational Patterns
Singleton: Single instance, thread-safe implementation
Factory: Object creation abstraction, factory method vs abstract factory
Builder: Step-by-step object construction, fluent interfaces
Structural & Behavioral
Repository: Data access abstraction, testability
Unit of Work: Transactional consistency across repositories
Strategy Pattern: Interchangeable algorithms, dependency injection
CQRS: Command Query Responsibility Segregation, separate read/write models
Mediator Pattern: MediatR library, decoupled request handling
</details>

<a id="microservices"></a>9. Microservices
<details>
<summary>▶️ Expand Topics</summary>

Architecture & Communication
Microservice Architecture: Bounded contexts, independent deployment
API Gateway: Routing, aggregation, cross-cutting concerns
Service Discovery: Client-side vs server-side discovery
Communication Patterns: Synchronous (HTTP/gRPC) vs asynchronous (messaging)
Messaging & Infrastructure
RabbitMQ: Exchanges, queues, bindings, message durability
Kafka Basics: Topics, partitions, producers, consumers
Docker Basics: Images, containers, Dockerfile, docker-compose
Kubernetes Basics: Pods, deployments, services, ingress
Distributed Caching: Redis cluster, cache-aside pattern
Event-Driven Architecture: Event sourcing, CQRS, eventual consistency
</details>

<a id="cloud-devops"></a>10. Cloud & DevOps
<details>
<summary>▶️ Expand Topics</summary>

Azure Services
Azure Basics: Resource groups, regions, RBAC, pricing
Azure App Services: Web Apps, deployment slots, scaling
Azure Functions: Serverless, triggers, bindings, durable functions
Azure Storage: Blobs, files, queues, tables
CI/CD & Deployment
CI/CD: Pipeline concepts, stages, gates, approvals
GitHub Actions: Workflows, jobs, steps, secrets
Azure DevOps: Pipelines, repos, boards, artifacts
Docker: Multi-stage builds, image optimization, registries
Kubernetes: Helm charts, config maps, secrets, autoscaling
IIS Deployment: Web.config, application pools, deployment scripts
</details>

<a id="testing"></a>11. Testing
<details>
<summary>▶️ Expand Topics</summary>

Testing Strategies
Unit Testing: Arrange-Act-Assert, test isolation, naming conventions
xUnit / NUnit: Attributes, assertions, fixtures, theory tests
Mocking: Moq framework, mocking interfaces, verifying calls
Integration Testing: Test server, in-memory databases, API clients
Test-Driven Development (TDD): Red-Green-Refactor cycle
</details>

<a id="security-dotnet"></a>12. Security
<details>
<summary>▶️ Expand Topics</summary>

Core Concepts
Authentication vs Authorization: Who you are vs what you can do
JWT: Structure, signing algorithms, token validation
OAuth: Delegated authorization, scopes, refresh tokens
HTTPS: TLS/SSL, certificate management, HSTS
Web Security
CORS: Cross-Origin Resource Sharing, policies, preflight requests
SQL Injection Prevention: Parameterized queries, ORM usage
XSS Prevention: Output encoding, Content Security Policy
CSRF Protection: Anti-forgery tokens, same-site cookies
Secure Password Storage: Hashing (bcrypt, PBKDF2), salting, peppering
</details>

<a id="performance-dotnet"></a>13. Performance Optimization
<details>
<summary>▶️ Expand Topics</summary>

Caching & Async
Caching: In-memory, distributed, cache invalidation strategies
Redis: Data structures, pub/sub, clustering
Response Compression: GZIP, Brotli, middleware configuration
Async Programming: Avoiding sync-over-async, ConfigureAwait(false)
Database & Memory
Database Optimization: Indexing, query tuning, connection pooling
Memory Optimization: Object pooling, ArrayPool<T>, reducing allocations
API Performance Tuning: Pagination, field filtering, HTTP/2, caching headers
</details>

<a id="architecture-dotnet"></a>14. Architecture & Best Practices
<details>
<summary>▶️ Expand Topics</summary>

Architectural Styles
Clean Architecture: Dependencies inward, use cases, entities
Onion Architecture: Domain-centric, infrastructure as plugin
Layered Architecture: Presentation, business, data access layers
DDD Basics: Entities, value objects, aggregates, domain events
Principles
SOLID Principles: (Recap with .NET examples)
DRY Principle: Avoiding duplication, shared libraries
KISS Principle: Simplicity in design and implementation
</details>

<a id="realtime-dotnet"></a>15. Real-Time & Messaging
<details>
<summary>▶️ Expand Topics</summary>

SignalR: Hubs, groups, connection management, scaling with Redis
WebSockets: Low-level API, handshake, binary/text frames
RabbitMQ: Advanced patterns (RPC, fanout, topic exchanges)
Azure Service Bus: Queues vs topics, sessions, dead-lettering
Kafka Basics: Consumer groups, offset management, exactly-once semantics
</details>

🔹 REACT JS
<a id="react-fundamentals"></a>1. React Fundamentals
<details>
<summary>▶️ Expand Topics</summary>

Core Concepts
What is React?: Component-based UI library, declarative programming
Virtual DOM: Diffing algorithm, reconciliation, performance benefits
Real DOM vs Virtual DOM: Why virtual DOM is faster for updates
JSX: Syntax extension, compilation to React.createElement()
Components & Data Flow
Components: Reusable UI building blocks
Functional Components: Modern approach with hooks
Class Components: Legacy lifecycle methods (for context)
Props: Immutable data passed from parent to child
State: Mutable data managed within component
Event Handling: Synthetic events, binding context
Conditional Rendering: &&, ternary, early returns
Lists and Keys: Rendering arrays, key prop importance
Forms in React: Controlled vs uncontrolled components
Controlled Components: Form data handled by React state
Uncontrolled Components: Form data handled by DOM refs
</details>

<a id="react-hooks"></a>2. React Hooks
<details>
<summary>▶️ Expand Topics</summary>

Built-in Hooks
useState: Managing local state, functional updates
useEffect: Side effects, cleanup, dependency array
useContext: Consuming context without prop drilling
useReducer: Complex state logic, action dispatching
useMemo: Memoizing expensive calculations
useCallback: Memoizing functions to prevent re-renders
useRef: Accessing DOM, storing mutable values
Custom Hooks: Extracting reusable logic, naming convention (useX)
Rules & Lifecycle
Hook Rules: Only call at top level, only in React functions
Hook Lifecycle: How hooks map to mount/update/unmount phases
</details>

<a id="react-lifecycle"></a>3. Component Lifecycle
<details>
<summary>▶️ Expand Topics</summary>

Class Component Lifecycle
Mounting: constructor, render, componentDidMount
Updating: shouldComponentUpdate, render, componentDidUpdate
Unmounting: componentWillUnmount
Functional Components with Hooks
Lifecycle Methods: Mapping componentDidMount → useEffect(() => {}, [])
Functional Component Lifecycle using Hooks: Cleanup functions, dependency management
</details>

<a id="state-management"></a>4. State Management
<details>
<summary>▶️ Expand Topics</summary>

Local vs Global
Local State: useState, component-scoped data
Global State: Context API, Redux, Zustand
Solutions
Context API: createContext, useContext, avoiding prop drilling
Redux Basics: Store, actions, reducers, connect/useSelector
Redux Toolkit: createSlice, configureStore, simplified Redux
Redux Thunk: Async actions, middleware
Redux Saga Basics: Generator functions, side effect management
Zustand Basics: Minimalist state management, hooks API
State Normalization: Flat state structure, entity tables
</details>

<a id="react-routing"></a>5. React Routing
<details>
<summary>▶️ Expand Topics</summary>

React Router: BrowserRouter, Routes, Route
Dynamic Routing: URL parameters, useParams
Nested Routes: Layout routes, outlet components
Route Parameters: :id, useParams, useSearchParams
Protected Routes: Authentication checks, redirect logic
Navigation: useNavigate, Link, programmatic navigation
Lazy Loading Routes: React.lazy, Suspense, code splitting
</details>

<a id="api-integration"></a>6. API Integration
<details>
<summary>▶️ Expand Topics</summary>

HTTP Clients
Fetch API: Native browser API, promises, error handling
Axios: Interceptors, defaults, cancellation
Patterns & Best Practices
API Calls using useEffect: Dependency arrays, cleanup
Error Handling: Try/catch, error boundaries, user feedback
Loading States: Skeleton screens, spinners, optimistic UI
Authentication APIs: Login flow, token storage, protected requests
Token Handling: Headers, interceptors, token refresh logic
Refresh Tokens: Silent refresh, rotation, security considerations
🎟️ Join The Writer's Circle event – Share your React journey!
</details>

<a id="performance-react"></a>7. Performance Optimization
<details>
<summary>▶️ Expand Topics</summary>

Rendering Optimization
React.memo: Preventing unnecessary re-renders of components
useMemo: Caching computed values
useCallback: Caching function references
Avoiding Re-renders: Proper dependency arrays, key props
Code Splitting & Loading
Code Splitting: React.lazy, dynamic import()
Lazy Loading: Components, routes, images
Suspense: Fallback UI during async operations
Advanced Techniques
Virtualization: react-window, react-virtualized for long lists
Debouncing: Delaying function execution (search inputs)
Throttling: Limiting function call frequency (scroll events)
</details>

<a id="advanced-react"></a>8. Advanced React Concepts
<details>
<summary>▶️ Expand Topics</summary>

Component Patterns
Higher Order Components (HOC): Wrapping components for reuse
Render Props: Sharing code via prop functions
Compound Components: Flexible component APIs (e.g., <Select><Option /></Select>)
Portals: Rendering children outside DOM hierarchy
Error Boundaries: Catching JS errors in component tree
Deep Dives
Context API Deep Dive: Performance considerations, multiple contexts
Reconciliation: How React updates the DOM efficiently
Fiber Architecture Basics: Incremental rendering, prioritization
Forward Ref: Passing refs through components
Controlled vs Uncontrolled Components: When to use which
</details>

<a id="forms-react"></a>9. Forms & Validation
<details>
<summary>▶️ Expand Topics</summary>

Form Libraries
Form Handling: Native React forms, controlled components
Formik: Form state, validation, submission handling
React Hook Form: Performance-focused, uncontrolled approach
Yup Validation: Schema-based validation, async rules
Advanced Forms
Dynamic Forms: Generating fields from configuration
File Upload Forms: FormData, progress tracking, preview
</details>

<a id="auth-react"></a>10. Authentication & Security
<details>
<summary>▶️ Expand Topics</summary>

JWT Authentication: Storing tokens, attaching to requests
Role-Based Access: Conditional rendering, route protection
Protected Routes: Higher-order components, wrapper logic
Token Storage: localStorage vs httpOnly cookies trade-offs
XSS Prevention: Sanitizing user input, avoiding dangerouslySetInnerHTML
Secure API Calls: HTTPS, token refresh, error handling
CORS Understanding: Browser security, server configuration
</details>

<a id="styling-react"></a>11. Styling in React
<details>
<summary>▶️ Expand Topics</summary>

CSS Approaches
CSS Modules: Scoped styles, [name].module.css
SCSS: Variables, nesting, mixins with React
Styled Components: CSS-in-JS, theming, dynamic props
Tailwind CSS: Utility-first, responsive design, JIT compiler
Material UI: Component library, theming, customization
Responsive Design: Media queries, mobile-first, flexbox/grid
</details>

<a id="typescript-react"></a>12. TypeScript with React
<details>
<summary>▶️ Expand Topics</summary>

TypeScript Basics
TypeScript Basics: Types, interfaces, generics
Props Typing: interface Props {}, React.FC<Props>
State Typing: useState<Type>, union types
Interfaces vs Types: When to use which
Generic Components: Reusable components with type parameters
API Integration
API Response Typing: Defining response shapes, error types
Type Safety: End-to-end type safety from API to UI
</details>

<a id="react-testing"></a>13. React Testing
<details>
<summary>▶️ Expand Topics</summary>

Testing Tools
Jest: Test runner, assertions, mocking
React Testing Library: User-centric testing, queries
Unit Testing: Testing pure functions, hooks
Component Testing: Rendering, interactions, accessibility
Advanced Testing
Mocking APIs: msw, jest.mock, fetch mocks
Snapshot Testing: UI regression detection, updating snapshots
</details>

<a id="build-deploy-react"></a>14. Build & Deployment
<details>
<summary>▶️ Expand Topics</summary>

Build Tools
Vite: Fast dev server, HMR, production builds
Webpack Basics: Loaders, plugins, code splitting
Babel Basics: Transpiling JSX, polyfills, presets
Deployment
Environment Variables: .env, process.env, build-time vs runtime
Production Build: Optimization, minification, source maps
Deployment Process: Static hosting, CDN, cache invalidation
Netlify: Drag-and-drop, CI/CD, redirects
Vercel: Serverless functions, edge network, preview deployments
Docker for React: Multi-stage builds, nginx serving, containerization
</details>

<a id="architecture-react"></a>15. React Architecture & Best Practices
<details>
<summary>▶️ Expand Topics</summary>

Project Structure
Folder Structure: Feature-based vs type-based organization
Reusable Components: Design system, prop interfaces, documentation
Separation of Concerns: UI, logic, data layers
Code Quality
Clean Code: Naming, functions, comments, DRY
Custom Hooks Architecture: Extracting logic, testing hooks
Error Handling Strategy: Boundaries, user feedback, logging
API Service Layer: Centralized HTTP client, error handling
Environment Configurations: Dev/staging/prod settings
</details>

<a id="realtime-react"></a>16. Real-Time Features
<details>
<summary>▶️ Expand Topics</summary>

WebSockets: useEffect setup, message handling, reconnection
SignalR with React: .NET backend integration, hub connections
Live Notifications: Toasts, badges, real-time updates
Chat Applications: Message history, typing indicators, presence
</details>

<a id="react-backend"></a>17. React + Backend Integration
<details>
<summary>▶️ Expand Topics</summary>

React with .NET API: CORS, proxy configuration, base URLs
Authentication Flow: Login, token storage, protected routes
API Token Management: Interceptors, refresh logic, logout
CRUD Operations: Form handling, optimistic updates, error states
Pagination: Server-side pagination, page controls
Search and Filters: Query parameters, debounced input, URL sync
</details>

🔹 SQL MASTERY
<a id="sql-fundamentals"></a>1. SQL Fundamentals
<details>
<summary>▶️ Expand Topics</summary>

Core Concepts
What is SQL?: Structured Query Language, relational databases
Types of SQL Commands:
DDL: CREATE, ALTER, DROP, TRUNCATE
DML: INSERT, UPDATE, DELETE, MERGE
DCL: GRANT, REVOKE
TCL: COMMIT, ROLLBACK, SAVEPOINT
Data Types: INT, VARCHAR, DATETIME, DECIMAL, BIT
Constraints:
Primary Key: Unique identifier, non-null
Foreign Key: Referential integrity
Unique Key: Enforce uniqueness
Check Constraint: Validate data rules
Default Constraint: Fallback values
Not Null: Require data presence
</details>

<a id="db-design"></a>2. Database Design
<details>
<summary>▶️ Expand Topics</summary>

Database Normalization:
1NF: Atomic values, no repeating groups
2NF: Remove partial dependencies
3NF: Remove transitive dependencies
BCNF: Stronger 3NF variant
Denormalization: When to break normalization for performance
ER Diagrams: Entities, attributes, relationships visualization
Relationships:
One-to-One: Rare, split sensitive data
One-to-Many: Most common (e.g., User → Orders)
Many-to-Many: Junction tables (e.g., Students ↔ Courses)
</details>

<a id="crud-sql"></a>3. CRUD Operations
<details>
<summary>▶️ Expand Topics</summary>

INSERT: Adding new records, VALUES, INSERT INTO ... SELECT
UPDATE: Modifying existing data, WHERE clause importance
DELETE: Removing records, soft deletes vs hard deletes
SELECT: Retrieving data, * vs explicit columns
MERGE: Upsert operations (insert or update)
</details>

<a id="sql-queries"></a>4. SQL Queries
<details>
<summary>▶️ Expand Topics</summary>

WHERE Clause: Filtering rows, operators (=, >, LIKE, IN)
ORDER BY: Sorting results, ASC/DESC, multiple columns
GROUP BY: Aggregating data, combining with aggregate functions
HAVING: Filtering groups (post-aggregation)
DISTINCT: Removing duplicate rows
TOP / LIMIT: Restricting result set size
BETWEEN: Range filtering (inclusive)
IN: Matching against a list of values
EXISTS: Subquery existence check
ANY and ALL: Comparing against subquery results
</details>

<a id="joins"></a>5. Joins
<details>
<summary>▶️ Expand Topics</summary>

INNER JOIN: Matching rows in both tables
LEFT JOIN: All left table rows + matches from right
RIGHT JOIN: All right table rows + matches from left
FULL OUTER JOIN: All rows from both tables
SELF JOIN: Joining table to itself (e.g., employee hierarchy)
CROSS JOIN: Cartesian product (use with caution)
Difference Between Joins: Venn diagrams, use cases, performance
</details>

<a id="sql-functions"></a>6. Functions
<details>
<summary>▶️ Expand Topics</summary>

Aggregate Functions
COUNT, SUM, AVG, MIN, MAX
String Functions
CONCAT, SUBSTRING, REPLACE, UPPER, LOWER, LEN
Date Functions
GETDATE(), DATEADD, DATEDIFF, FORMAT
Mathematical Functions
ROUND, CEILING, FLOOR, ABS, POWER
User Defined Functions (UDF)
Scalar functions, table-valued functions, performance considerations
</details>

<a id="subqueries"></a>7. Subqueries
<details>
<summary>▶️ Expand Topics</summary>

Nested Queries: Subqueries in SELECT, FROM, WHERE
Correlated Subqueries: Reference outer query, row-by-row execution
Scalar Subqueries: Return single value
EXISTS vs IN: Performance differences, null handling
</details>

<a id="views"></a>8. Views
<details>
<summary>▶️ Expand Topics</summary>

Simple Views: Virtual tables from SELECT queries
Complex Views: Joins, aggregations, subqueries
Indexed Views: Materialized views for performance (SQL Server)
Advantages and Limitations: Security, simplicity vs update restrictions
</details>

<a id="stored-procedures"></a>9. Stored Procedures
<details>
<summary>▶️ Expand Topics</summary>

Creating Procedures: CREATE PROCEDURE, parameters
Input Parameters: Passing values into procedures
Output Parameters: Returning values via parameters
Error Handling: TRY...CATCH, RAISERROR, THROW
Dynamic SQL: sp_executesql, parameterization to prevent injection
Procedure Optimization: Execution plan caching, recompilation hints
</details>

<a id="triggers"></a>10. Triggers
<details>
<summary>▶️ Expand Topics</summary>

AFTER Trigger: Executes after DML operation
INSTEAD OF Trigger: Replaces DML operation (useful for views)
DML Triggers: INSERT, UPDATE, DELETE triggers
Trigger Use Cases: Auditing, validation, cascading logic
⚠️ Caution: Hidden logic, performance impact, debugging difficulty
</details>

<a id="indexes"></a>11. Indexes
<details>
<summary>▶️ Expand Topics</summary>

Clustered Index: Physical data order, one per table
Non-Clustered Index: Separate structure with pointers
Composite Index: Multiple columns, column order matters
Unique Index: Enforces uniqueness
Index Seek vs Scan: Performance implications
Index Fragmentation: Causes, detection, rebuilding/reorganizing
Index Optimization: Covering indexes, filtered indexes, included columns
</details>

<a id="transactions-sql"></a>12. Transactions
<details>
<summary>▶️ Expand Topics</summary>

ACID Properties:
Atomicity: All or nothing
Consistency: Valid state transitions
Isolation: Concurrent transaction separation
Durability: Committed changes persist
BEGIN TRANSACTION, COMMIT, ROLLBACK
SAVEPOINT: Partial rollback points
Nested Transactions: @@TRANCOUNT, behavior in SQL Server
</details>

<a id="locks-concurrency"></a>13. Locks & Concurrency
<details>
<summary>▶️ Expand Topics</summary>

Locking: Shared (S), exclusive (X), update (U) locks
Blocking: One transaction waiting for another's lock
Deadlocks: Circular wait, detection, victim selection
Isolation Levels:
Read Uncommitted: Dirty reads allowed
Read Committed: Default, no dirty reads
Repeatable Read: Prevents non-repeatable reads
Serializable: Full isolation, range locks
Snapshot: Versioning, optimistic concurrency
</details>

<a id="cte"></a>14. Common Table Expressions (CTE)
<details>
<summary>▶️ Expand Topics</summary>

Simple CTE: Improving query readability, modularization
Recursive CTE: Hierarchical data (org charts, trees)
CTE vs Temp Table: Scope, reusability, performance trade-offs
</details>

<a id="temp-objects"></a>15. Temporary Objects
<details>
<summary>▶️ Expand Topics</summary>

Temporary Tables: #temp (session), ##global (all sessions)
Global Temp Tables: Cross-session visibility, cleanup considerations
Table Variables: @table, scope, statistics limitations
</details>

<a id="advanced-sql"></a>16. Advanced SQL Concepts
<details>
<summary>▶️ Expand Topics</summary>

Window Functions
ROW_NUMBER: Unique row numbering
RANK / DENSE_RANK: Ranking with/without gaps
LEAD and LAG: Accessing next/previous row values
PARTITION BY: Window framing for calculations
Pivoting Data
Pivot and Unpivot: Transforming rows to columns and vice versa
Dynamic Pivot: Building pivot queries dynamically
</details>

<a id="performance-sql"></a>17. Performance Optimization
<details>
<summary>▶️ Expand Topics</summary>

Query Optimization: SARGable queries, avoiding functions on columns
Execution Plan: Reading operators, cost estimation, warnings
SQL Profiler: Tracing queries, identifying bottlenecks
Index Tuning: Missing index suggestions, unused index removal
Avoiding Full Table Scan: Proper indexing, selective predicates
Query Refactoring: Simplifying logic, breaking complex queries
Statistics: Auto-update, manual updates, impact on optimizer
Parameter Sniffing: Causes, solutions (OPTION (RECOMPILE), local variables)
</details>

<a id="security-sql"></a>18. Security
<details>
<summary>▶️ Expand Topics</summary>

SQL Injection Prevention: Parameterized queries, stored procedures, ORM usage
Roles and Permissions: Principle of least privilege
GRANT and REVOKE: Managing access at object level
Encryption Basics: TDE, column-level encryption, Always Encrypted
</details>

<a id="backup-recovery"></a>19. Backup & Recovery
<details>
<summary>▶️ Expand Topics</summary>

Full Backup: Complete database copy
Differential Backup: Changes since last full backup
Transaction Log Backup: Point-in-time recovery, log truncation
Restore Process: Full + differential + log sequence, testing restores
</details>

<a id="sql-architecture"></a>20. SQL Server Architecture
<details>
<summary>▶️ Expand Topics</summary>

SQL Server Components: Database Engine, Agent, SSIS, SSRS, SSAS
Database Files: .mdf (data), .ldf (log), filegroups
TempDB: System database for temporary objects, optimization tips
Memory Management: Buffer pool, plan cache, memory grants
Buffer Pool: Data page caching, read-ahead, lazy writer
</details>

<a id="etl-data"></a>21. ETL & Data Handling
<details>
<summary>▶️ Expand Topics</summary>

Import and Export Data: Wizard, bcp, BULK INSERT
Bulk Insert: High-volume data loading, options (TABLOCK, BATCHSIZE)
SSIS Basics: Packages, control flow, data flow, error handling
Data Migration: Strategies (big bang vs incremental), validation, rollback
</details>
