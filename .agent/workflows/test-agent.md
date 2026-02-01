# AGENT SELF-TEST WORKFLOW

## 1. KERNEL CHECK

- **Goal**: Verify Protocol Zero.
- **Action**: Ping `mcp-context7`.
  - _Pass_: Tool responds.
  - _Fail_: Tool error (Stop execution).

## 2. MEMORY WRITE CHECK

- **Goal**: Verify artifact persistence.
- **Action**:
  1.  Create `.agent/artifacts/test_token.md` with content "Write Check".
  2.  Read the file back.
  3.  Delete the file.
  - _Pass_: File created, read, and deleted.

## 3. LOGIC SIMULATION (DRY RUN)

- **Goal**: Verify Architect -> Builder handoff without writing code.
- **Action**:
  1.  **Architect**: Simulate stack detection (Read root files).
  2.  **Architect**: Update `tech_stack.md` (Dry run - do not overwrite if valid).
  3.  **Builder**: Check if `conventions.md` exists and is readable.

## 4. REPORTING

- **Output**:

  ```text
  AGENT OS DIAGNOSTIC REPORT
  --------------------------
  [OK] Kernel (Context7 connected)
  [OK] Memory (Read/Write access verified)
  [OK] Logic Chain (Architect -> Builder path valid)
  [OK] Rules (Active Stack: [Detected Stack])

  SYSTEM IS READY FOR OPERATION.
  ```