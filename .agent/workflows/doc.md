# DOCUMENTATION GENERATION WORKFLOW

1.  **Input**:
    - Ask user: "What type of documentation?" (Options: README, Swagger, Internal Wiki, User Guide).
    - Ask user: "Target directory?" (Default: root or `docs/`).

2.  **Skill Activation**: Call **Tech Writer Skill**.

3.  **Process**:
    - **Tech Writer** scans the codebase.
    - **Tech Writer** reads `.agent/artifacts/tech_stack.md` to understand the context.
    - **Tech Writer** generates the content.

4.  **Verification**:
    - If generating Swagger/OpenAPI, validate the YAML syntax.

5.  **Output**:
    - Write file to disk.
    - Report: "Documentation generated at [Path]."