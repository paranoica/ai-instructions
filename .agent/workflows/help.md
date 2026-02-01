# SYSTEM HELP MENU

## 1. ANALYSIS

1.  **Read Artifacts**: Load `.agent/artifacts/tech_stack.md`.
2.  **Check Context**: Check if `.agent/company/STRATEGY.md` exists (Enterprise Mode).

## 2. OUTPUT GENERATION

Display the following dashboard in a Markdown Code Block:

```text
+--------------------------------------------------+
|               AGENT OS v1.0                      |
+--------------------------------------------------+
| ACTIVE STACK: [Language] / [Framework]           |
| MEMORY STATE: [Task Status]                      |
+--------------------------------------------------+

AVAILABLE COMMANDS:

[ STRATEGY & PRODUCT (Optional) ]
  /startup   CEO: Validate idea & define Strategy
  /spec      CPO: Create Product Requirements (PRD)
  /promote   CMO: Marketing & Release Notes
  /verify-release CISO: Final Security Veto Check

[ DEVELOPMENT (Standard) ]
  /feature   Start a new feature cycle (Research -> Plan -> Code)
  /prompt    Convert rough idea into engineering spec

[ MAINTENANCE ]
  /fix       Medic: Iteratively fix bugs and TypeScript types
  /format    Janitor: Enforce snake_case, tabs(4), remove comments
  /refactor  Perform safe architectural refactoring

[ INFRASTRUCTURE (DEVOPS) ]
  /infra     Ops: K8s, Nginx, Kafka, RabbitMQ, Docker setup
  /db-migrate DBA: Safe schema changes and migrations
  /docker-build Ops: Build, optimize, and scan container images

[ ANALYSIS & SYSTEM ]
  /audit     Sherlock: Security & Architecture review (OWASP)
  /info      Deep system diagnostic (Context7 & Stack check)
  /summary   Show session progress, changed files, and next steps
  /commit    Git Manager: Generate semantic commit
  /help      Show this menu

USAGE:
  Type command in chat. Example: "/feature user login"
```