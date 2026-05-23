# 📘 ASP.NET Core Complete Interview & Learning Roadmap

> A comprehensive, topic-by-topic checklist for mastering ASP.NET Core. Check off items as you progress. Each topic includes expanded subtopics, key concepts, and interview focus areas.

## 📊 Progress Tracker
| Category | Status | Notes |
|----------|--------|-------|
| Core Fundamentals | ⬜ Not Started | |
| Controllers & Routing | ⬜ Not Started | |
| Model Binding & Validation | ⬜ Not Started | |
| Middleware & Pipeline | ⬜ Not Started | |
| Dependency Injection | ⬜ Not Started | |
| Configuration & Options | ⬜ Not Started | |
| Authentication & Authorization | ⬜ Not Started | |
| API Design & REST | ⬜ Not Started | |
| Entity Framework Core | ⬜ Not Started | |
| Async Programming & Performance | ⬜ Not Started | |
| Testing Strategies | ⬜ Not Started | |
| Background Services & Messaging | ⬜ Not Started | |
| Security Best Practices | ⬜ Not Started | |
| Deployment & DevOps | ⬜ Not Started | |
| Advanced Patterns & Architecture | ⬜ Not Started | |
| Modern .NET 8/9 Features | ⬜ Not Started | |
| Interview Prep & System Design | ⬜ Not Started | |

---

## 🌱 1. Core Fundamentals
- [ ] **.NET Runtime & CLR**
  - Managed vs unmanaged code, JIT compilation, AOT (Native AOT in .NET 8)
  - Garbage collection generations, finalizers, `IDisposable` pattern
  - Value types vs reference types, boxing/unboxing performance impact
- [ ] **ASP.NET Core Hosting Model**
  - `Program.cs` minimal hosting vs startup class pattern (legacy)
  - `WebApplication` builder, `IHost`, `IWebHost`, `IApplicationBuilder`
  - Kestrel vs IIS vs HTTP.sys: when to use each, reverse proxy patterns
- [ ] **Request Pipeline Overview**
  - Order matters: middleware executes in registration order
  - Short-circuiting: `context.Response.WriteAsync()` + `return`
  - Branching: `Map`, `MapWhen`, `UseWhen` for conditional pipelines
- [ ] **Configuration System**
  - `IConfiguration`: hierarchical key-value, multiple providers (JSON, env vars, secrets)
  - `appsettings.json` + environment-specific overrides (`appsettings.Production.json`)
  - User secrets (dev), Azure Key Vault (prod), command-line args precedence
- [ ] **Logging & Diagnostics**
  - `ILogger<T>` abstraction, structured logging, log levels
  - Serilog integration: sinks, enrichers, correlation IDs
  - Activity/`DiagnosticSource` for distributed tracing (OpenTelemetry)

---

## 🛣️ 2. Controllers & Routing
- [ ] **Controller Basics**
  - `[ApiController]` attribute: automatic 400 responses, binding source inference
  - Action return types: `IActionResult`, `ActionResult<T>`, typed results
  - HTTP verb attributes: `[HttpGet]`, `[HttpPost]`, `[HttpPut]`, `[HttpDelete]`, `[HttpPatch]`
- [ ] **Routing Strategies**
  - Conventional routing: `{controller=Home}/{action=Index}/{id?}`
  - Attribute routing: `[Route("api/[controller]")]`, `[Route("{id}")]`
  - Route constraints: `int`, `guid`, `regex`, custom `IRouteConstraint`
- [ ] **Advanced Routing**
  - Area routing for modular apps (`[Area("Admin")]`)
  - Endpoint routing: `UseRouting()` + `UseEndpoints()`, middleware ordering
  - Dynamic segments, catch-all routes (`{*slug}`), optional parameters
- [ ] **Model Binding Sources**
  - `[FromBody]`, `[FromQuery]`, `[FromRoute]`, `[FromForm]`, `[FromHeader]`
  - Complex type binding, collection binding, custom model binders
  - Binding prefixes, `BindingSource` customization, `IValueProvider`

---

## 🔍 3. Model Binding & Validation
- [ ] **Data Annotations**
  - `[Required]`, `[StringLength]`, `[Range]`, `[RegularExpression]`, `[EmailAddress]`
  - Custom validation attributes: inherit `ValidationAttribute`, override `IsValid`
  - `IValidatableObject` interface for cross-property validation
- [ ] **FluentValidation Integration**
  - `AbstractValidator<T>`, rule chains, custom rules, async validation
  - ASP.NET Core pipeline integration: `AddFluentValidationAutoValidation()`
  - Localization, conditional rules, collection validation
- [ ] **Validation Pipeline**
  - Automatic model state checking in `[ApiController]`
  - Manual `ModelState.IsValid` checks, custom error formatting
  - ProblemDetails RFC 7807: standardized error responses
- [ ] **Advanced Binding Scenarios**
  - Binding to interfaces/abstract classes with custom binders
  - File uploads: `IFormFile`, `IFormFileCollection`, streaming large files
  - Complex nested objects, polymorphic deserialization (`JsonPolymorphicAttribute`)

---

## ⚙️ 4. Middleware & Pipeline
- [ ] **Built-in Middleware**
  - `UseExceptionHandler`, `UseHsts`, `UseHttpsRedirection`, `UseStaticFiles`
  - `UseRouting`, `UseAuthorization`, `UseEndpoints`, `UseAuthentication`
  - Order dependency: auth must come after routing, before endpoints
- [ ] **Custom Middleware**
  - Inline: `app.Use(async (ctx, next) => { ... })`
  - Class-based: `IMiddleware` interface or convention-based `InvokeAsync`
  - Constructor injection vs `InvokeAsync` parameters (scoped services caution)
- [ ] **Middleware Patterns**
  - Global exception handling: capture, log, return ProblemDetails
  - Request/response logging: correlation IDs, timing, sanitization
  - Rate limiting: `AddRateLimiter()`, fixed window, token bucket, custom policies
- [ ] **Pipeline Branching & Short-Circuiting**
  - `Map` for path-based branching (e.g., `/health`, `/metrics`)
  - `MapWhen` for predicate-based branching (e.g., API vs MVC)
  - Short-circuit: return early without calling `next()` (auth failures, cached responses)

---

## 🔌 5. Dependency Injection (DI)
- [ ] **Service Lifetimes**
  - `Transient`: new instance every request (lightweight, stateless)
  - `Scoped`: one instance per HTTP request (DB contexts, unit of work)
  - `Singleton`: one instance for app lifetime (caches, config, thread-safe services)
  - Captive dependencies: never inject scoped into singleton (memory leaks)
- [ ] **Registration Patterns**
  - `AddTransient<TService, TImplementation>()`, `AddScoped`, `AddSingleton`
  - Factory registration: `AddTransient<T>(provider => new T(...))`
  - Open generic registration: `AddTransient(typeof(IRepository<>), typeof(Repository<>))`
- [ ] **Advanced DI Scenarios**
  - Conditional registration: `AddTransient<T>(...)` based on config/env
  - Decorator pattern: register implementation, then wrap with decorator
  - Keyed services (.NET 8+): `AddKeyedTransient<T>(key, implementation)`
- [ ] **Service Location & Anti-Patterns**
  - Avoid `IServiceProvider.GetService<T>()` (service locator anti-pattern)
  - Constructor injection preferred; property injection only for optional deps
  - `ActivatorUtilities` for framework-level dynamic resolution (rare)

---

## ⚙️ 6. Configuration & Options Pattern
- [ ] **IConfiguration Deep Dive**
  - Provider precedence: command line > env vars > secrets > JSON files
  - Reload-on-change: `AddJsonFile(path, reloadOnChange: true)`
  - Section binding: `Configuration.GetSection("MySection").Get<T>()`
- [ ] **IOptions<T> Pattern**
  - `IOptions<T>`: singleton, read-only, loaded at startup
  - `IOptionsSnapshot<T>`: scoped, reloads per request (for mutable config)
  - `IOptionsMonitor<T>`: singleton with change callbacks, thread-safe
- [ ] **Validation & Hierarchical Config**
  - `[Required]` on options properties + `Services.AddOptions<T>().ValidateDataAnnotations()`
  - Custom validation: `.Validate(obj => obj.Port > 0, "Port must be positive")`
  - Nested options: `DatabaseOptions` inside `AppSettings`, binding strategies
- [ ] **Environment-Specific Configuration**
  - `IWebHostEnvironment`: `IsDevelopment()`, `IsProduction()`, content root
  - `appsettings.{Environment}.json` merging, environment variable overrides
  - Azure App Configuration, AWS Parameter Store integration patterns

---

## 🔐 7. Authentication & Authorization
- [ ] **Authentication Schemes**
  - Cookie authentication: login flow, persistent cookies, sliding expiration
  - JWT Bearer tokens: issuance, validation, refresh token patterns
  - OAuth 2.0 / OpenID Connect: external providers (Google, Azure AD, Auth0)
- [ ] **ASP.NET Core Identity**
  - `UserManager<T>`, `SignInManager<T>`, role/claim management
  - Custom user/store implementations, two-factor authentication, lockout
  - Identity UI scaffolding vs custom Razor Pages/Blazor integration
- [ ] **Authorization Policies**
  - Role-based: `[Authorize(Roles = "Admin")]`
  - Policy-based: `AddAuthorization(opts => opts.AddPolicy("RequireEmployee", ...))`
  - Requirement handlers: `IAuthorizationRequirement`, `AuthorizationHandler<T>`
- [ ] **Advanced Security Patterns**
  - Claims transformation: `IClaimsTransformation` for enriching principal
  - Resource-based authorization: `IAuthorizationService.AuthorizeAsync(user, resource, policy)`
  - API key authentication: custom `AuthenticationHandler<T>`, header validation

---

## 🌐 8. API Design & REST Best Practices
- [ ] **REST Principles**
  - Resource naming: plural nouns, nested resources (`/users/{id}/orders`)
  - HTTP semantics: `200 OK`, `201 Created`, `204 No Content`, `400/401/403/404/500`
  - Idempotency: `PUT` vs `PATCH`, `POST` for non-idempotent operations
- [ ] **Versioning Strategies**
  - URL path: `/api/v1/products`, `/api/v2/products`
  - Query string: `/api/products?api-version=1.0`
  - Header: `api-version: 1.0`, content negotiation
  - ASP.NET Core Versioning library: `AddApiVersioning()`, deprecation headers
- [ ] **OpenAPI / Swagger**
  - `Swashbuckle.AspNetCore`: `AddSwaggerGen()`, `UseSwagger()`, `UseSwaggerUI()`
  - XML comments for operation descriptions, `[ProducesResponseType]` annotations
  - JWT auth in Swagger: `AddSecurityDefinition`, `OperationFilter` for Bearer header
- [ ] **Pagination, Filtering, Sorting**
  - Query params: `?page=1&pageSize=20&sort=name&filter=status:active`
  - `OData` or custom expression parsing, `IQueryable` composition
  - Metadata responses: `X-Pagination` header, `PageInfo` in response body
- [ ] **HATEOAS & Hypermedia**
  - Adding `links` array to responses: `rel`, `href`, `method`
  - `IActionLinkGenerator` patterns, `UrlHelper` for route generation
  - When to use: public APIs, discoverability; when to skip: internal microservices

---

## 🗄️ 9. Entity Framework Core (Data Access)
- [ ] **DbContext & Configuration**
  - `OnConfiguring` vs `AddDbContext<T>(options => ...)` in DI
  - Connection strings: `options.UseSqlServer(Configuration.GetConnectionString("Default"))`
  - Migrations: `Add-Migration`, `Update-Database`, `Script-Migration` for production
- [ ] **Modeling & Relationships**
  - Fluent API: `modelBuilder.Entity<T>().HasKey()`, `.HasOne().WithMany()`
  - Owned types, value conversions, shadow properties, backing fields
  - Concurrency tokens: `[Timestamp]`, `RowVersion`, `IsConcurrencyToken()`
- [ ] **Querying Strategies**
  - LINQ to Entities: `Where`, `Select`, `Include`, `ThenInclude`, `AsNoTracking`
  - Split queries vs single query: `AsSplitQuery()` for N+1 mitigation
  - Raw SQL: `FromSqlInterpolated`, `SqlQuery<T>`, parameterization to prevent injection
- [ ] **Performance Optimization**
  - Compiled queries: `EF.CompileQuery`, `EF.CompileAsyncQuery` for hot paths
  - Batch operations: `ExecuteUpdate`, `ExecuteDelete` (.NET 7+), `BulkExtensions`
  - Connection resiliency: `EnableRetryOnFailure()`, circuit breaker patterns
- [ ] **Advanced Patterns**
  - Repository + Unit of Work: when to abstract EF Core, when not to
  - Global query filters: soft delete (`IsDeleted`), multi-tenancy
  - Interceptors: `SaveChangesInterceptor`, `CommandInterceptor` for logging/auditing

---

## ⚡ 10. Async Programming & Performance
- [ ] **Async/Await Fundamentals**
  - `Task` vs `ValueTask`, `ConfigureAwait(false)` in library code
  - Avoiding `async void`, proper exception propagation, `Task.WhenAll`
  - Cancellation tokens: `CancellationTokenSource`, cooperative cancellation
- [ ] **I/O-Bound vs CPU-Bound**
  - I/O: `await db.SaveChangesAsync()`, `await httpClient.GetAsync()` (scales threads)
  - CPU: `Task.Run(() => HeavyComputation())` (offloads to thread pool)
  - `Parallel.ForEachAsync` (.NET 6+) for concurrent I/O with degree of parallelism
- [ ] **Caching Strategies**
  - In-memory cache: `IMemoryCache`, absolute/sliding expiration, cache dependencies
  - Distributed cache: `IDistributedCache` + Redis/SQL Server, serialization
  - Response caching: `[ResponseCache]`, `UseResponseCaching()`, VaryBy headers
- [ ] **Profiling & Diagnostics**
  - MiniProfiler, Application Insights, OpenTelemetry integration
  - `dotnet-counters`, `dotnet-trace`, `dotnet-dump` for production diagnostics
  - BenchmarkDotNet for micro-benchmarks, avoiding premature optimization

---

## 🧪 11. Testing Strategies
- [ ] **Unit Testing Foundations**
  - xUnit vs NUnit vs MSTest: `[Fact]`, `[Theory]`, `[InlineData]`, `[ClassData]`
  - Moq/NSubstitute: mocking `IRepository<T>`, `ILogger<T>`, `IHttpClientFactory`
  - Arrange-Act-Assert pattern, test naming conventions, isolation principles
- [ ] **Integration Testing**
  - `WebApplicationFactory<T>`: in-memory test server, custom `ConfigureTestServices`
  - Test databases: `UseInMemoryDatabase()` (limited), Testcontainers for real SQL Server
  - Auth mocking: `OverrideAuthentication()`, fake JWT tokens, policy bypass
- [ ] **End-to-End & Contract Testing**
  - Playwright/Cypress for UI flows (Blazor/MVC), API contract tests with `PactNet`
  - Snapshot testing: `Verify.XUnit` for JSON responses, approval testing
  - Performance/load testing: k6, JMeter, `Microsoft.Crank` for CI pipelines
- [ ] **Test-Driven Development (TDD)**
  - Red-Green-Refactor cycle, writing tests before implementation
  - Mocking external dependencies early, designing for testability (SOLID)
  - When TDD adds value vs when it slows down (prototypes, UI-heavy features)

---

## 🔄 12. Background Services & Messaging
- [ ] **Hosted Services**
  - `IHostedService`: `StartAsync`/`StopAsync`, graceful shutdown
  - `BackgroundService`: `ExecuteAsync` loop, `CancellationToken` handling
  - Registering: `services.AddHostedService<MyService>()`
- [ ] **Queues & Messaging**
  - Azure Service Bus: `ServiceBusClient`, topics/subscriptions, dead-letter queues
  - RabbitMQ: `IConnection`, `IModel`, exchange types, durable queues
  - MassTransit/Rebus: abstraction layers, sagas, retry policies, monitoring
- [ ] **Hangfire & Recurring Jobs**
  - Dashboard setup, job filters, retries, expiration
  - Recurring jobs: `RecurringJob.AddOrUpdate<T>(...)`, cron expressions
  - Storage: SQL Server, Redis, PostgreSQL backends
- [ ] **Real-Time with SignalR**
  - Hubs: `Hub<T>`, client methods, group management, user targeting
  - Scale-out: Azure SignalR Service, Redis backplane for multiple instances
  - Security: authentication/authorization on hub methods, connection validation

---

## 🛡️ 13. Security Best Practices
- [ ] **Input Validation & Sanitization**
  - Never trust client input: validate on server even if client validates
  - HTML encoding: Razor auto-encodes, `@Html.Raw()` risks, `HtmlEncoder`
  - SQL injection prevention: parameterized queries, EF Core LINQ safety
- [ ] **Authentication Hardening**
  - JWT: short expiration, refresh tokens, secure storage (HttpOnly cookies)
  - Password policies: complexity, hashing (PBKDF2, bcrypt, Argon2), salting
  - MFA enforcement, account lockout, suspicious activity detection
- [ ] **Authorization & Least Privilege**
  - Role/claim design: avoid over-privileged roles, use policies for granularity
  - Resource ownership checks: `if (order.UserId != currentUser.Id) return Forbid()`
  - API-level authorization: `[Authorize(Policy = "CanEditOrder")]` on actions
- [ ] **Secure Configuration & Secrets**
  - Never commit secrets: user secrets (dev), Azure Key Vault/AWS Secrets Manager (prod)
  - HTTPS enforcement: `UseHsts()`, `UseHttpsRedirection()`, CSP headers
  - Dependency scanning: `dotnet list package --vulnerable`, Snyk, Dependabot

---

## 🚀 14. Deployment & DevOps
- [ ] **Publishing & Packaging**
  - `dotnet publish -c Release -r linux-x64 --self-contained true/false`
  - Single-file publish, trimming (ILLink), Native AOT (.NET 8+)
  - Docker: multi-stage builds, minimal base images (`mcr.microsoft.com/dotnet/aspnet:8.0-alpine`)
- [ ] **CI/CD Pipelines**
  - GitHub Actions: build, test, publish to Azure/AWS, migration scripts
  - Azure DevOps: YAML pipelines, service connections, approval gates
  - Database migrations in CI: `dotnet ef database update` vs scripted deployments
- [ ] **Cloud Deployment Patterns**
  - Azure App Service: slots, deployment slots, auto-scaling, custom domains
  - Azure Container Apps / AKS: Kubernetes manifests, Helm charts, service mesh
  - AWS: Elastic Beanstalk, ECS/Fargate, API Gateway + Lambda (.NET 8 AOT)
- [ ] **Monitoring & Observability**
  - Application Insights: custom events, dependencies, exceptions, live metrics
  - OpenTelemetry: traces, metrics, logs export to Jaeger, Prometheus, Grafana
  - Health checks: `AddHealthChecks()`, `/health` endpoint, Kubernetes probes

---

## 🏗️ 15. Advanced Patterns & Architecture
- [ ] **Clean Architecture / Onion Architecture**
  - Layers: Domain, Application, Infrastructure, Presentation (API/UI)
  - Dependency rule: inner layers never reference outer layers
  - Use cases / CQRS: commands vs queries, separate models for write/read
- [ ] **MediatR & Vertical Slice Architecture**
  - `IRequest<T>`, `IRequestHandler<T>`, pipeline behaviors (logging, validation, caching)
  - Feature folders: `/Features/Orders/PlaceOrder/`, co-locating related code
  - Benefits: easier navigation, independent deployability, reduced coupling
- [ ] **Domain-Driven Design (DDD) Basics**
  - Entities vs Value Objects: identity vs structural equality
  - Aggregates & Aggregate Roots: consistency boundaries, repository per aggregate
  - Domain Events: `INotificationHandler<T>`, eventual consistency patterns
- [ ] **Microservices Patterns**
  - API Gateway: Ocelot, YARP, Azure API Management for routing/aggregation
  - Service discovery: Consul, Kubernetes services, DNS-based resolution
  - Resilience: Polly policies (retry, circuit breaker, timeout, fallback)
- [ ] **Event-Driven Architecture**
  - Outbox pattern: reliable event publishing with transactional consistency
  - Saga pattern: distributed transactions via choreography/orchestration
  - Event sourcing: storing state changes as events, projection rebuilding

---

## 🆕 16. Modern .NET 8/9 Features
- [ ] **.NET 8 Highlights**
  - Native AOT: ahead-of-time compilation, smaller binaries, faster startup
  - Minimal APIs enhancements: endpoint filters, typed results, OpenAPI auto-gen
  - Performance: `System.IO.Pipelines`, `Span<T>`, `Memory<T>` optimizations
- [ ] **.NET 9 Preview / Upcoming**
  - Enhanced OpenAPI support: `MapOpenApi()`, schema generation improvements
  - Dynamic loading improvements, improved reflection performance
  - Blazor United (if applicable): unified SSR/interactive rendering model
- [ ] **C# 12 Features for ASP.NET**
  - Primary constructors for services: `public MyService(ILogger logger) { ... }`
  - Collection expressions: `int[] ids = [1, 2, 3];`, `List<int> list = [.. existing, 4];`
  - `ref readonly` parameters, `inline` arrays for high-performance scenarios
- [ ] **Tooling & Developer Experience**
  - `dotnet watch` hot reload for APIs, `dotnet dev-certs https --trust`
  - `dotnet user-secrets`, `dotnet sql-cache`, `dotnet ef` CLI enhancements
  - IDE: JetBrains Rider, VS 2022, VS Code C# Dev Kit, GitHub Copilot integration

---

## 🎯 17. Interview Prep & System Design
- [ ] **Coding Interview Drills**
  - Build a minimal API with CRUD, validation, auth, and EF Core in <45 mins
  - Implement a custom middleware (logging, rate limiting, exception handling)
  - Write a repository with async methods, unit tests, and integration test setup
- [ ] **System Design Scenarios**
  - Design a URL shortener: API contract, DB schema, caching, scaling strategy
  - Real-time dashboard: SignalR hubs, background aggregation, client reconnection
  - Multi-tenant SaaS: database-per-tenant vs schema-per-tenant, isolation, billing
- [ ] **Behavioral & Architecture Questions**
  - "How would you migrate a monolith to microservices?" (strangler fig, bounded contexts)
  - "How do you handle database schema changes in production?" (migrations, blue/green)
  - "Describe a time you debugged a production performance issue" (tools, methodology)
- [ ] **Code Review Checklist**
  - Security: authZ checks, input validation, secrets handling, dependency versions
  - Performance: async all the way, N+1 queries, caching strategy, bundle size
  - Maintainability: naming, SOLID, test coverage, documentation, logging clarity
- [ ] **Mock Interview Questions**
  - *Explain the ASP.NET Core request pipeline and middleware ordering.*
  - *How do you prevent over-posting/mass assignment vulnerabilities?*
  - *When would you choose Dapper over EF Core? What are the tradeoffs?*
  - *How does dependency injection lifetime affect scalability?*
  - *Design an API for file uploads with progress tracking and virus scanning.*

---

## 📌 How to Use This Checklist
1. **Track Progress**: Replace `⬜ Not Started` in the tracker with `✅ Done` as you complete sections.
2. **Learn in Order**: Follow the sequence. Later topics build on earlier foundations.
3. **Code Along**: Every concept should be implemented in a small project or GitHub repo.
4. **Interview Prep**: Use the expanded subtopics to generate flashcards. Practice explaining each out loud in <60 seconds.
5. **Stay Updated**: .NET evolves rapidly. Bookmark the [.NET Blog](https://devblogs.microsoft.com/dotnet/) and [ASP.NET Core Docs](https://learn.microsoft.com/aspnet/core/) for .NET 9 updates.

> 💡 *Tip: Don't just memorize. Build a small full-stack app (React + ASP.NET Core API + T-SQL) using at least 3 patterns from this list. Real implementation beats theoretical knowledge in interviews.*

> 🔗 *Cross-Stack Bonus*: When studying React topics, implement the frontend for your ASP.NET API. When studying T-SQL, write the queries your API endpoints will execute. Full-stack context makes you 10x more valuable.
