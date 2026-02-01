---
description: Run a deep diagnostic of the Agent OS, checking memory, tools, and rules.
---

# SYSTEM DIAGNOSTIC WORKFLOW

1.  **Identity Check**: Confirm `GEMINI.md` is active and Protocol Zero (Anti-Hallucination) is engaged.

2.  **Tool Check**: Ping `mcp-context7`.
    - _Result:_ [v] Connected / [x] Error (Critical)

3.  **Stack Detection & Rule Activation**:
    - Scan root directory for signature files:
      - `package.json` -> Activate Web Stack (`10-stack-web.md`).
      - `nest-cli.json` -> Activate Backend Stack (`11-stack-backend.md`).
      - `pubspec.yaml` / `go.mod` -> Activate Mobile/System Stack (`12-stack-mobile.md`).
      - `requirements.txt` / `pyproject.toml` -> Activate Python Stack (`13-stack-python.md`).
      - `Cargo.toml` -> Activate Rust Stack (`14-stack-rust.md`).
      - `pom.xml` / `build.gradle` -> Activate Java Stack (`15-stack-java.md`).
    - **Action**: Update `.agent/artifacts/tech_stack.md` with the detected language and framework.

4.  **Memory Check**:
    - Validate `.agent/artifacts/plan.md` against schema.
    - Validate `.agent/artifacts/tech_stack.md` against schema.

5.  **Report**:
    - Output system health status.
    - List active Rule Sets.