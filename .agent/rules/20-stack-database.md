# DATABASE ENGINEERING STANDARDS

Activation: Glob(**/\*.prisma, **/schema.sql, **/migrations/\*, **/\*.entity.ts, docker-compose.yml)

## 1. SCHEMA DESIGN

- **Naming Convention**:
  - Tables: `snake_case`, plural (e.g., `users`, `order_items`).
  - Columns: `snake_case` (e.g., `created_at`, `user_id`).
  - Indexes: `idx_tablename_columnname`.
- **Primary Keys**: Use UUIDv7 or CUID2 for distributed systems. Avoid auto-increment integers unless strictly necessary for legacy reasons.
- **Audit Fields**: Every table must have `created_at` (immutable) and `updated_at` (auto-update).
- **Constraints**: Enforce foreign keys and unique constraints at the database level, not just in application code.

## 2. ORM & MIGRATIONS (PRISMA / TYPEORM)

- **Source of Truth**: The schema definition (e.g., `schema.prisma`) is the absolute source of truth.
- **Migrations**:
  - NEVER edit the database schema manually in the GUI/Console.
  - All changes must be versioned migrations.
  - Review generated SQL before applying.
- **Context7 Protocol**: Before writing any query, you MUST use `mcp-context7` to read the current state of the schema file. Do not hallucinate column names.

## 3. PERFORMANCE

- **Indexing**: Add indexes for all foreign keys and columns used in `WHERE`, `ORDER BY`, or `JOIN` clauses.
- **N+1 Protection**: Use `include` (Prisma) or `relations` (TypeORM) carefully. Prefer data-loader patterns for GraphQL.
- **Connections**: Use connection pooling (e.g., PgBouncer) in serverless environments.