# FEATURE DEVELOPMENT WORKFLOW

1.  **Initialization**:
    - Clear `artifacts/task.md`.
    - Ask user for Feature Name and Requirements.

2.  **Research Phase (Architect)**:
    - Call `mcp-context7` to fetch docs for relevant libraries.
    - Check `tech_stack.md` for constraints.

3.  **Planning Phase (Architect)**:
    - Draft a plan in `artifacts/plan.md`.
    - **STOP**: Present plan to user. Wait for "Proceed".

4.  **Implementation Phase (Builder)**:
    - For each step in plan:
      1.  Write Code (adhering to Rules).
      2.  Call **Janitor** (auto-format new code).
      3.  Verify (Build/Test).
      4.  Update `task.md`.

5.  **Completion**:
    - Run final **Medic** check (ensure no type errors).
    - Report "Feature Complete".