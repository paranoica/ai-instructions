# Coding Conventions & Style Guide

This file serves as the Single Source of Truth for code styling in this project.
**Agent Instruction:** All code generated or modified MUST adhere to these rules strictly.

## 1. Formatting

- **Indentation:** Use **TABS** (set to display width of 4 spaces). NEVER use spaces for indentation.
- **Quotes:** Use **DOUBLE QUOTES** (`"`) for all strings. Replace single quotes (`'`) unless they are part of a template literal or strictly required by the language syntax (e.g., specific char types in some languages).
- **Whitespace:** NO extra or unreasonable whitespace. Keep code compact but readable. Remove trailing whitespace.
- **Semicolons:** Follow the mandatory syntax of the active language. If optional (like in JS/TS), use them only if it prevents ambiguity, otherwise avoid clutter.

## 2. Naming Conventions

- **Preference:** `snake_case`.
  - Variables: `user_id`, `api_response`, `is_valid`.
  - Files: `user_controller.ts`, `login_screen.dart`.
  - _Exception:_ If the framework STRICTLY enforces another style (e.g., React Components must be `PascalCase`), follow the framework constraint for that specific identifier only, but keep internal logic variables in `snake_case`.

## 3. Comments & Hygiene

- **Strict Rule:** NO COMMENTS allowed in the final code.
  - Remove `//`, `/* ... */`, `<!-- ... -->`, `{/* ... */}`.
  - _Exception:_ Documentation comments that are required for library generation (e.g., GoDocs, JSDocs for exported API) are permitted ONLY if explicitly requested.
- **Logs:** NO `console.log`, `print`, `fmt.Println` allowed in production code. Remove all debug prints.

## 4. TypeScript Specifics (if applicable)

- **Typing Strategy:**
  - Avoid `any` at all costs.
  - If a type cannot be strictly determined immediately:
    - Use `unknown` if safety is priority.
    - Use `// TODO: fix type` annotation (temporarily allowed) if complex refactoring is needed later.
- **Imports:** Use absolute paths (alias `@/`) where configured.