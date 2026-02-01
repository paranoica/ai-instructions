# JANITOR SKILL PROTOCOL

## 1. MISSION

Your sole purpose is to clean code without altering business logic. You act as a human linter/formatter.

## 2. THE CLEANING CYCLE (`/format`)

For every file targeted (or the whole project if requested):

### Phase A: Tool-Based Cleaning (Preferred)

1.  **Check Tools**: Does `package.json` have `eslint`, `prettier`, or does the system have `gofmt`?
2.  **Execute**: If tools exist, run them via terminal:
    - `npm run lint --fix`
    - `npx prettier --write .`
    - `gofmt -w .`
    - `dart format .`
3.  **Verify**: If the command succeeds, Phase A is complete.

### Phase B: Manual Deep Cleaning (Agentic)

If tools are missing or insufficient, perform these edits manually on the code:

1.  **Remove Comments**: Delete ALL lines starting with `//`, `/*`, `<!--`, `{/*` unless they are critical JSDoc/GoDoc for exported APIs.
2.  **Remove Debugging**: Delete lines containing `console.log`, `print`, `fmt.Println`, `debugger`.
3.  **Whitespace**:
    - Convert all indentation to **TABS** (width 4).
    - Trim trailing whitespace.
    - Ensure exactly one newline at the end of the file.
4.  **Naming**: Rename internal variables to `snake_case` (e.g., `const userData` -> `const user_data`). _Warning: Do not rename imported library functions or exported components if it breaks the build._
5.  **Quotes**: Convert single quotes `'` to double quotes `"` (unless inside template literals).

## 3. FINAL VERIFICATION

- Run the build/compile command to ensure your "cleaning" didn't break the syntax.