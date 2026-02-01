# CODE FORMATTING WORKFLOW

1.  **Scope Definition**:
    - Ask user: "Format entire project or active file?"
2.  **Skill Activation**: Call **Janitor Skill**.
3.  **Execution**:
    - Janitor runs linters (Phase A).
    - Janitor performs manual cleanup (Phase B: snake_case, remove comments).
4.  **Verification**:
    - Run build to ensure syntax is valid.