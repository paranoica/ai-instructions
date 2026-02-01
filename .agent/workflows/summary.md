# SESSION SUMMARY WORKFLOW

1.  **Data Acquisition**:
    - **Memory**: Read `.agent/artifacts/task.md`. Extract the "Goal" and list items marked as completed `[x]`.
    - **Filesystem**: Execute `git status -s`. List modified/added files.
    - **Architecture**: Read `.agent/artifacts/adr.md` (check if new records were added today).

2.  **Synthesis (Architect Skill)**:
    - Compare "Planned" (Task) vs "Actual" (Git).
    - Identify any drift (files changed but not in plan).

3.  **Report Generation**:
    Output a structured text report:

    ```text
    SESSION REPORT
    ==============
    GOAL: [Goal from task.md]
    STATUS: [In Progress / Completed]

    COMPLETED TASKS:
    - [Task 1]
    - [Task 2]

    FILES TOUCHED:
    - [src/file_a.ts]
    - [src/file_b.ts]

    ARCHITECTURAL CHANGES:
    - [New ADRs if any]

    NEXT STEPS:
    - [Suggestion based on remaining unchecked items]
    ```

4.  **Cleanup**:
    - Ask user: "Do you want to clear the current task memory for a new session?"
    - If yes, reset `task.md`.