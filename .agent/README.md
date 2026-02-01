# Agent OS

This repository is equipped with an autonomous Agent Operating System located in the `.agent/` directory.
It transforms any Agent-Driven IDE into a multi-role development team (Architect, DevOps, Security, Builder) with an optional C-Suite layer.

## Documentation

**[Read the Operator Manual (INSTRUCTIONS.md)](INSTRUCTIONS.md)** for detailed usage guide in English and Russian.

## Architecture

The system is divided into layers:

1.  **Kernel**: `GEMINI.md` defines the "Protocol Zero" (Anti-Hallucination via Context7).
2.  **Memory**: `artifacts/*.md` provide persistent context.
3.  **Brain**: Orchestrates requests based on the detected stack.
4.  **Skills**: Specialized roles defined in `skills/`.
5.  **C-Suite**: (Optional) Strategic agents (CEO, CPO, CMO) for full product lifecycle management.

## Supported Stacks (Auto-Detected)

- **Web**: React, Next.js, Node.js (`package.json`)
- **Backend**: NestJS (`nest-cli.json`)
- **Mobile**: Flutter (`pubspec.yaml`)
- **System**: Go (`go.mod`), Rust (`Cargo.toml`)
- **Scripting**: Python (`requirements.txt`)
- **Enterprise**: Java/Spring (`pom.xml`)

## Command Reference

| Command             | Role        | Description                                             |
| :------------------ | :---------- | :------------------------------------------------------ |
| **STRATEGY**        |             |                                                         |
| **/startup**        | CEO         | Analyzes idea, market viability & creates Strategy.     |
| **/spec**           | CPO         | Converts Strategy into PRD & User Stories.              |
| **/promote**        | CMO         | Generates release notes and marketing content.          |
| **/verify-release** | CISO        | Final security veto check before deployment.            |
| **DEV & OPS**       |             |                                                         |
| **/feature**        | Builder     | Starts development cycle: Research -> Plan -> Code.     |
| **/prompt**         | Architect   | Converts a vague idea into a detailed engineering spec. |
| **/fix**            | Medic       | Fixes bugs and enforces strict types (No `any`).        |
| **/format**         | Janitor     | Enforces style: Tabs(4), snake_case, removes comments.  |
| **/audit**          | Sherlock    | Performs Security (OWASP) and Architecture audit.       |
| **/infra**          | Ops         | Scaffolds K8s, Nginx, Kafka, RabbitMQ, Docker.          |
| **/db-migrate**     | DBA         | Safely manages database migrations.                     |
| **DOCS & SYSTEM**   |             |                                                         |
| **/doc**            | Tech Writer | Generates README, Swagger/OpenAPI, or Wikis.            |
| **/test-agent**     | System      | Runs a logic simulation to verify IDE integration.      |
| **/info**           | System      | Checks agent health, active stack, and memory status.   |
| **/summary**        | Architect   | Summarizes session progress and file changes.           |
| **/help**           | System      | Shows the list of available commands.                   |
| **/commit**         | Git Manager | Generates semantic commits.                             |