---
description: Display the main menu of available commands and current system status.
---

# SYSTEM HELP MENU

## 1. ANALYSIS

1.  **Read Artifacts**: Load `.agent/artifacts/tech_stack.md`.
2.  **Read Workflows**: List all available `.md` files in `.agent/workflows/`.

## 2. OUTPUT GENERATION

Display the following dashboard in a Markdown Code Block:

```text
+--------------------------------------------------+
|                   AGENT OS v1.0                  |
+--------------------------------------------------+
| ACTIVE STACK: [Language] / [Framework]           |
| MEMORY STATE: [Task Status]                      |
+--------------------------------------------------+

AVAILABLE COMMANDS:

[ DEVELOPMENT ]
  /feature   Start a new feature cycle (Research -> Plan -> Code)
  /prompt    Convert rough idea into engineering spec

[ MAINTENANCE ]
  /fix       Medic: Iteratively fix bugs and TypeScript types
  /format    Janitor: Enforce snake_case, tabs(4), remove comments
  /refactor  Perform safe architectural refactoring

[ ANALYSIS & REPORTING ]
  /audit     Sherlock: Security & Architecture review (OWASP)
  /info      Deep system diagnostic (Context7 & Stack check)
  /summary   Show session progress, changed files, and next steps
  /help      Show this menu

[ VERSION CONTROL ]
  /commit    Git Manager: Generate semantic commit from staged diff

USAGE:
  Type command in chat. Example: "/feature user login"
```