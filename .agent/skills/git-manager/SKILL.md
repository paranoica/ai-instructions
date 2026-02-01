# GIT MANAGER SKILL PROTOCOL

## 1. MISSION

Analyze code changes and synthesize a semantic, descriptive commit message.

## 2. ANALYSIS PROTOCOL (`/commit`)

1.  **Input Acquisition**:
    - Execute: `git diff --staged` (or `git diff --cached`).
    - If output is empty, Execute: `git diff` (and warn user that nothing is staged).
    - **Context7 Check**: If the diff is too large, use `mcp-context7` to summarize the specific files changed.

2.  **Categorization Strategy (Conventional Commits)**:
    Determine the `type` based on the nature of changes:
    - `feat`: A new feature (correlates with `.agent/workflows/feature.md`).
    - `fix`: A bug fix (correlates with `.agent/workflows/fix.md`).
    - `style`: Formatting, missing semi colons, etc. (correlates with `.agent/workflows/format.md`).
    - `refactor`: Restructuring code without changing behavior.
    - `docs`: Documentation only.
    - `chore`: Maintainance, deps, config.

3.  **Formatting Rules**:
    - **Structure**: `<type>(<scope>): <subject>`
    - **Scope**: The module or file affected (e.g., `auth`, `user_controller`, `ui`).
    - **Subject**: Use imperative mood ("add" not "added"). Lowercase. No period at end.
    - **Body** (Optional): Bullet points explaining _why_, not _what_.

## 3. EXAMPLE OUTPUTS

- `feat(auth): implement google oauth provider`
- `fix(user_service): handle null pointer in get_user`
- `style(all): enforce snake_case and tab indentation`

## 4. EXECUTION

- Present the suggested message to the user.
- Ask: "Commit with this message?"