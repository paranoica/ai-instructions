# AGENT OS: OPERATOR MANUAL

This document provides a detailed guide on how to operate the Agent OS embedded in this repository. It explains the purpose of each command, the underlying logic, and the best practices for collaboration with the AI workforce.

---

## 1. CORE CONCEPTS

### The Architecture

You are not working with a simple chatbot. You are working with a **Multi-Role Team**.

- **Kernel**: Prevents hallucinations. If the Agent doesn't know a library version, it looks it up (Context7).
- **Memory**: The Agent remembers your tech stack and current plan between sessions via the `.agent/artifacts/` folder.
- **Strictness**: Code style (snake_case, tabs) is enforced programmatically.

### The Workflow

The ideal development loop follows this pattern:

1.  **Initialize**: `/info` (Detect stack).
2.  **Define**: `/prompt` (Clarify requirements).
3.  **Build**: `/feature` (Plan -> Code -> Verify).
4.  **Polish**: `/fix` (Debug) -> `/format` (Style) -> `/audit` (Security).
5.  **Save**: `/commit` (Git).

---

## 2. COMMAND REFERENCE

### System Commands

#### `/info`

- **Context**: Use at the start of a session or when opening a new project.
- **Action**: Performs a deep diagnostic.
  1.  Checks connection to Context7 tools.
  2.  Scans project files (`package.json`, `requirements.txt`) to activate the correct Rule Set.
  3.  Validates the integrity of the Memory (artifacts).
- **Output**: System Health Report.

#### `/help`

- **Context**: When you forget a command.
- **Action**: Displays the main menu and current status.

#### `/summary`

- **Context**: Use before taking a break or finishing work.
- **Action**: Compares the `task.md` (Plan) against `git status` (Reality).
- **Output**: A report listing completed tasks, modified files, and recommended next steps.

### Development Commands

#### `/prompt <raw_idea>`

- **Context**: When you have a vague idea (e.g., "I need a payment system").
- **Action**: The **Architect** analyzes your stack and requirements to generate a rigorous Engineering Spec.
- **Why use it**: It prevents the "garbage in, garbage out" problem.

#### `/feature <description>`

- **Context**: The main command for writing code.
- **Action**:
  1.  **Research**: Calls external docs to verify APIs.
  2.  **Plan**: Writes a step-by-step plan to `artifacts/plan.md`.
  3.  **Approve**: Waits for your confirmation.
  4.  **Execute**: Writes code, tests, and updates the task tracker.

### Maintenance Commands

#### `/fix`

- **Context**: When you see a red squiggly line, a build error, or a `any` type.
- **Action**: The **Medic** runs a loop: Analyze Error -> Research Library Types -> Apply Strict Fix -> Verify.
- **Note**: It aggressively removes `any` types and replaces them with strict Interfaces.

#### `/format`

- **Context**: Before committing code.
- **Action**: The **Janitor** enforces the project style guide (`artifacts/conventions.md`).
  - Converts spaces to Tabs (4).
  - Renames variables to `snake_case`.
  - Removes all comments and console logs.

#### `/audit`

- **Context**: Before deploying or merging a PR.
- **Action**: The **Sherlock** skill scans for:
  - Security vulnerabilities (OWASP).
  - Performance bottlenecks (N+1 queries).
  - Architectural violations.
- **Output**: A read-only report. It does not modify code.

### DevOps & Infrastructure

#### `/infra`

- **Context**: When setting up the environment.
- **Action**: Scaffolds configurations for Docker, Kubernetes, Nginx, Kafka, or RabbitMQ based on best practices.

#### `/db-migrate`

- **Context**: When you need to change the database structure.
- **Action**: Safely modifies the schema file and generates a migration script. Prevents data loss.

#### `/docker-build`

- **Context**: To verify the application container.
- **Action**: Builds the image, optimizes layers, and runs vulnerability scans.

### Version Control

#### `/commit`

- **Context**: When work is done and verified.
- **Action**: Generates a Semantic Commit Message (e.g., `feat(auth): add login`) based on staged changes and commits them.

---

# РУКОВОДСТВО ОПЕРАТОРА (Russian)

Это документ описывает, как управлять Агентной ОС (Agent OS).

## 1. Основные Концепции

### Архитектура

Вы работаете не с чат-ботом, а с **Командой Ролей**:

- **Ядро**: Защищает от выдумок (галлюцинаций). Агент обязан проверять версии библиотек через Context7.
- **Память**: Папка `.agent/artifacts/` хранит контекст (планы, стек, решения) между сессиями.
- **Строгость**: Стиль кода (snake_case, табы) применяется автоматически.

### Рабочий Процесс

1.  **Старт**: `/info` (Определение стека).
2.  **Задача**: `/prompt` (Уточнение ТЗ).
3.  **Код**: `/feature` (План -> Код -> Тест).
4.  **Качество**: `/fix` (Баги) -> `/format` (Стиль) -> `/audit` (Безопасность).
5.  **Финал**: `/commit` (Гит).

---

## 2. СПРАВОЧНИК КОМАНД

### Системные

- `/info` — Диагностика. Проверяет инструменты и определяет, какой язык вы используете (Python, JS, Go).
- `/help` — Показать меню команд.
- `/summary` — Отчет за сессию. Что сделано, какие файлы затронуты.

### Разработка

- `/prompt <идея>` — **Архитектор** превращает вашу идею в детальное ТЗ с учетом текущего стека.
- `/feature <задача>` — **Строитель** начинает работу. Сначала читает документацию (чтобы не ошибиться в версиях), строит план, спрашивает разрешение, и только потом пишет код.

### Поддержка и Качество

- `/fix` — **Медик**. Исправляет ошибки компиляции и убирает типы `any`, заменяя их на строгие интерфейсы.
- `/format` — **Уборщик**. Приводит код к стандарту: Табы (4 пробела), snake_case, удаляет все комментарии и логи.
- `/audit` — **Шерлок**. Ищет уязвимости безопасности и проблемы производительности. Не правит код, только докладывает.

### Инфраструктура (DevOps)

- `/infra` — Создает конфиги для K8s, Nginx, Kafka, Redis.
- `/db-migrate` — **DBA**. Безопасно меняет схему базы данных и создает файлы миграций.
- `/docker-build` — Собирает и оптимизирует Docker-образ.

### Git

- `/commit` — Анализирует изменения и делает коммит с правильным описанием (например, `feat: ...` или `fix: ...`).