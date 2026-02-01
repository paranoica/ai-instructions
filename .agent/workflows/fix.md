# BUG FIXING WORKFLOW

1.  **Context Gathering**:
    - Do we have an error message? If no, run the build command (`npm run build` or equivalent) to capture stderr.
2.  **Skill Activation**: Call **Medic Skill**.
    - Pass the error logs and the relevant source files.
3.  **Execution Loop**:
    - The Medic will iterate (Fix -> Verify) up to 3 times.
4.  **Memory Update**:
    - If the fix required an architectural change, update `artifacts/adr.md`.