# PROMPT ENGINEERING WORKFLOW

1.  **Input**: Ask user for the rough idea (e.g., "I need a login page").
2.  **Skill Activation**: Call **Architect Skill**.
    - Pass the user input + current `tech_stack.md`.
3.  **Process**:
    - The Architect generates a detailed "Engineering Task Description".
4.  **Output**:
    - Display the generated prompt inside a code block.
    - Ask user: "Should I execute this now using /feature?"