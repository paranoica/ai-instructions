# DBA SKILL PROTOCOL

## 1. MISSION

Maintain data integrity, manage schema evolution, and optimize query performance.

## 2. MIGRATION PROTOCOL (`/db-migrate`)

When requested to modify the database:

1.  **Analyze State**:
    - Call `mcp-context7` to read the current schema (e.g., `prisma/schema.prisma`).
2.  **Plan Change**:
    - Draft the change in the schema file.
    - If renaming columns: Warn about data loss. Suggest a 2-step migration (add new -> copy data -> drop old).
3.  **Generate Migration**:
    - Command: `npx prisma migrate dev --name [descriptive_name]` (or equivalent).
4.  **Verify**:
    - Check the generated SQL file for destructive operations.

## 3. OPTIMIZATION PROTOCOL

When asked to optimize a slow query:

1.  **Analyze**: Ask for the query execution plan (EXPLAIN ANALYZE) if available.
2.  **Index Check**: Check if involved columns are indexed.
3.  **Recommendation**:
    - Suggest adding a composite index.
    - Suggest rewriting the query (e.g., removing wildcard `%` at start of string).