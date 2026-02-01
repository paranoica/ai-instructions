# SYSTEM DIAGNOSTIC WORKFLOW

1.  **Identity Check**: Confirm `GEMINI.md` is active and Protocol Zero (Anti-Hallucination) is engaged.
2.  **Tool Check**: Ping `mcp-context7`.
    - _Result:_ [v] Connected / [x] Error
3.  **Memory Check**:
    - Validate `.agent/artifacts/tech_stack.md` against schema.
    - Validate `.agent/artifacts/plan.md` against schema.
4.  **Rule Check**:
    - Identify which rule file is currently active (e.g., `10-stack-web.md`).
5.  **Report**:
    - Output a bulleted list of the system health.
    - If `tech_stack.md` is missing, trigger the **Architect Skill** to initialize the project.