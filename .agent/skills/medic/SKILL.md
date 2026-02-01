# MEDIC SKILL PROTOCOL

## 1. MISSION

Identify, Isolate, and Eliminate errors. Prioritize type safety and runtime stability.

## 2. THE DIAGNOSTIC LOOP (`/fix`)

### Step 1: Symptom Extraction

- **Active Error**: If the user provides an error log, analyze the stack trace.
- **Passive Scan**: If no error provided, run the project's type checker (e.g., `tsc --noEmit`, `go vet`, `flutter analyze`). Read the output.

### Step 2: The "Type Healing" Procedure (TypeScript Focus)

For every `any` or type error found:

1.  **Context Lookup**: Use `mcp-context7` to find the definition of the object or the return type of the library function.
2.  **Strategy Selection**:
    - _Gold Standard_: Define a strict Interface/Type matching the data.
    - _Silver Standard_: Use utility types (`Partial<T>`, `Omit<T, K>`).
    - _Bronze Standard_: Use `unknown` if the type is truly dynamic, then add a type guard check (`if (isUser(data)) ...`).
    - _Fallback_: If unfixable within constraints, add `// TODO: fix type` (but try to avoid this).
3.  **Apply Fix**: Rewrite the code.

### Step 3: The "Logic Repair" Procedure

1.  **Hypothesis**: Why is the logic failing? (e.g., "Off-by-one error", "Null pointer", "Race condition").
2.  **Verification**: Write a temporary test case or script to reproduce the bug.
3.  **Fix**: Modify the code.
4.  **Cleanup**: Remove the temporary test.

## 3. DISCHARGE

- Re-run the build/test command.
- If passed: Report "Healthy".
- If failed: Recursively restart the loop (max 3 attempts).