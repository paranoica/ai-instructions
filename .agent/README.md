# Agent OS

This repository is equipped with an autonomous Agent Operating System located in the `.agent/` directory.
It transforms any Agent-Driven IDE into a multi-role development team (Architect, DevOps, Security, Builder).

## Architecture

The system is divided into layers:

1.  **Kernel**: `GEMINI.md` defines the "Protocol Zero" (Anti-Hallucination via Context7).
2.  **Memory**: `artifacts/*.md` provide persistent context (Plans, Stack definitions, ADRs).
3.  **Brain**: `rules/00-brain.md` acts as the orchestrator, routing requests to specific skills.
4.  **Skills**: Specialized roles defined in `skills/`.

## Command Reference

| Command         | Role        | Description                                                     |
| :-------------- | :---------- | :-------------------------------------------------------------- |
| **/info**       | System      | Checks agent health, active stack, and memory status.           |
| **/help**       | System      | Shows the list of available commands.                           |
| **/summary**    | Architect   | Summarizes completed tasks and file changes in current session. |
| **/feature**    | Builder     | Starts development: Research (Context7) -> Plan -> Code.        |
| **/prompt**     | Architect   | Converts a vague user idea into a detailed engineering spec.    |
| **/fix**        | Medic       | Iteratively fixes errors, enforces strict types (no `any`).     |
| **/format**     | Janitor     | Enforces style: Tabs(4), snake_case, removes comments/logs.     |
| **/audit**      | Sherlock    | Performs a security (OWASP) and architecture audit.             |
| **/commit**     | Git Manager | Generates Conventional Commits based on staged changes.         |
| **/infra**      | Ops Manager | Scaffolds K8s, Nginx, Kafka, RabbitMQ configs.                  |
| **/db-migrate** | DBA         | Safely manages database schema and migrations.                  |

## Coding Standards (Enforced by Janitor)

- **Indentation**: Tabs (width 4).
- **Quotes**: Double quotes (`"`).
- **Naming**: `snake_case` for variables/files (unless framework mandates PascalCase).
- **Hygiene**: No comments, no console logs in production code.
- **Typing**: No `any`. Use strict interfaces or `unknown` with guards.

## Setup Guide

1.  **Clone**: Use this repository as a template.
2.  **Initialize**: Open in your IDE and run `/info`.
3.  **Develop**: Use `/feature` to build, `/infra` to deploy.