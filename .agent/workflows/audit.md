# SECURITY AUDIT WORKFLOW

1.  **Scope Definition**:
    - Target: Entire `src/` or `lib/` directory.
2.  **Skill Activation**: Call **Sherlock Skill**.
3.  **Execution**:
    - Sherlock scans for OWASP vulnerabilities.
    - Sherlock checks for `conventions.md` violations.
4.  **Report**:
    - Output the structured "Sherlock Audit Report" to the chat.
    - **Do not apply fixes automatically.** Wait for user command (e.g., "Fix criticals").