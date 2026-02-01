# DATABASE MIGRATION WORKFLOW

1.  **Input**:
    - Ask user: "What changes do you want to make to the schema?" (e.g., "Add phone number to User").

2.  **Skill Activation**: Call **DBA Skill**.

3.  **Safety Check**:
    - DBA checks if the change is destructive (dropping tables/columns).
    - If destructive, explicit confirmation is required: "This will delete data. Proceed?"

4.  **Execution**:
    - Modify schema file.
    - Run migration command.
    - Update strict TypeScript types (if using Prisma/TypeORM) via **Medic** skill logic.

5.  **Documentation**:
    - Update `artifacts/adr.md` if the database topology changes significantly.