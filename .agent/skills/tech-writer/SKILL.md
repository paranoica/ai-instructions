# TECH WRITER SKILL PROTOCOL

## 1. MISSION

Convert code logic into human-readable or machine-readable documentation.

## 2. DOCUMENTATION MODES (`/doc`)

### Mode A: API Specification (Swagger/OpenAPI)

1.  **Scan**: Analyze Controllers (NestJS) or Route Handlers (Next.js/Python).
2.  **Extract**: Identify endpoints, HTTP methods, request bodies (DTOs), and response types.
3.  **Generate**: Create/Update `openapi.yaml` or `swagger.json`.
4.  **Strictness**: Ensure types match the code exactly (no hallucinated fields).

### Mode B: Project Documentation (README/INSTRUCTIONS)

1.  **Analyze**: Read `package.json` (or equivalent) and `tech_stack.md`.
2.  **Draft**:
    - **Installation**: Exact commands (`npm install`, `go mod download`).
    - **Configuration**: List required Environment Variables.
    - **Usage**: Examples of how to run the app.
3.  **Output**: `README.md` or `docs/SETUP.md`.

### Mode C: Internal Wiki (Architecture)

1.  **Analyze**: Read `.agent/artifacts/adr.md` and folder structure.
2.  **Draft**: Explain the high-level architecture, module boundaries, and data flow.

## 3. STYLE GUIDE

- **Format**: Markdown (standard).
- **Language**: English (unless requested otherwise).
- **Tone**: Professional, concise, objective.