# BACKEND ENGINEERING STANDARDS (NESTJS)

Activation: Glob(nest-cli.json, src/**/\*.module.ts, src/**/\*.controller.ts)

## 1. NESTJS ARCHITECTURAL PATTERNS

- **Layered Architecture**: Strictly follow the Controller -> Service -> Repository pattern.
  - **Controllers**: Handle HTTP/RPC transport, DTO validation, and serialization. No business logic.
  - **Services**: Encapsulate pure business logic.
  - **Repositories**: Encapsulate database access queries.
- **Dependency Injection**:
  - Use Constructor Injection for all dependencies.
  - Do not use `@Inject()` unless resolving a specific token or handling circular dependencies with `forwardRef()`.
  - Use interfaces for service injection to enable easy mocking in tests.
- **Modules**: Group related components into feature modules. Use a `SharedModule` for common utilities.

## 2. VALIDATION AND SERIALIZATION

- **DTOs (Data Transfer Objects)**:
  - Create separate DTO classes for every input (Body, Query, Param).
  - Use `class-validator` decorators (`@IsString()`, `@IsInt()`, `@Min()`) for robust runtime validation.
  - Use `class-transformer` to transform raw JSON into typed class instances.
- **Response Serialization**:
  - Use Interceptors (e.g., `ClassSerializerInterceptor`) to sanitize responses (exclude passwords, format dates).
  - Never return raw database entities directly from controllers. Map them to Response DTOs.

## 3. DATABASE AND ORM PRACTICES

- **Transaction Management**: Use proper transaction boundaries. Ensure operations that must be atomic are wrapped in a transaction manager or query runner.
- **Query Optimization**:
  - Avoid N+1 query problems by using relations or data loaders.
  - Select only necessary fields (`.select(['id', 'name'])`).
- **Migration Safety**: Never synchronize schema (`synchronize: true`) in production. Always use generated migrations.

## 4. ERROR HANDLING AND OBSERVABILITY

- **Exceptions**: Throw standard HTTP exceptions (`NotFoundException`, `BadRequestException`) or custom domain exceptions extending them.
- **Filters**: Use Global Exception Filters to standardize the error response structure across the entire API.
- **Logging**: Use the built-in `Logger` service. Do not use `console.log`.