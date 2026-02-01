# COMMIT WORKFLOW

1.  **Pre-Flight Check**:
    - Ask user: "Have you run /format and /fix to ensure code quality?"
    - If yes, proceed.

2.  **Skill Activation**: Call **Git Manager Skill**.

3.  **Process**:
    - Git Manager analyzes `git diff --staged`.
    - Git Manager generates a semantic message.

4.  **Interaction**:
    - Output the message in a code block.
    - Command: `git commit -m "..."`
    - Ask user to confirm execution.

5.  **Memory Update**:
    - If this commit completes the current goal, update `.agent/artifacts/task.md` to `status: completed`.