# AGENT OS: OPERATOR MANUAL

This document provides a detailed guide on how to operate the Agent OS embedded in this repository. It explains the purpose of each command, the underlying logic, and the best practices for collaboration with the AI workforce.

---

## 1. CORE CONCEPTS

### The Architecture

You are not working with a simple chatbot. You are working with a Multi-Role Team.

- **Kernel**: Prevents hallucinations. If the Agent doesn't know a library version, it looks it up (Context7).
- **Memory**: The Agent remembers your tech stack and current plan between sessions via the .agent/artifacts/ folder.
- **Strictness**: Code style (snake_case, tabs) is enforced programmatically.

### The Workflow Modes

You can use the system in two ways:

1.  **Rapid Mode (Vibecoding)**: Jump straight to coding using feature, fix, and format commands.
2.  **Enterprise Mode (Startup Sim)**: Plan the business first using startup and spec commands, then execute.

---

## 2. COMMAND REFERENCE

### C-Suite Commands (Enterprise Mode)

#### /startup

- **Role**: CEO.
- **Action**: Critiques business viability, checks competitors, and creates a STRATEGY.md.

#### /spec

- **Role**: CPO.
- **Action**: Converts the Strategy into a detailed Product Requirements Document (PRD.md) with User Stories.

#### /promote

- **Role**: CMO.
- **Action**: Generates release notes, tweets, or blog posts based on the work done.

#### /verify-release

- **Role**: CISO.
- **Action**: Final security scan. Has VETO power to block release if critical bugs exist.

### Development Commands (Standard)

#### /prompt <raw_idea>

- **Role**: Architect.
- **Action**: Analyzes your stack and requirements to generate a rigorous Engineering Spec.

#### /feature <description>

- **Role**: Builder.
- **Action**:
  1.  **Research**: Calls external docs to verify APIs via Context7.
  2.  **Plan**: Writes a step-by-step plan to artifacts/plan.md.
  3.  **Approve**: Waits for your confirmation.
  4.  **Execute**: Writes code, tests, and updates the task tracker.

### Maintenance & Quality

#### /fix

- **Role**: Medic.
- **Action**: Runs a loop: Analyze Error -> Research Library Types -> Apply Strict Fix -> Verify.

#### /format

- **Role**: Janitor.
- **Action**: Enforces the project style guide (artifacts/conventions.md).
  - Converts spaces to Tabs (4).
  - Renames variables to snake_case.
  - Removes all comments and console logs.

#### /audit

- **Role**: Sherlock.
- **Action**: Scans for OWASP vulnerabilities and architectural violations. Output is read-only.

### DevOps & Infrastructure

#### /infra

- **Role**: Ops Manager.
- **Action**: Scaffolds configurations for Docker, Kubernetes, Nginx, Kafka, or RabbitMQ.

#### /db-migrate

- **Role**: DBA.
- **Action**: Safely modifies the schema file and generates a migration script.

### Documentation & System

#### /doc

- **Role**: Tech Writer.
- **Context**: When code is done but documentation is missing.
- **Action**: Generates Swagger/OpenAPI specs from code, updates README.md, or creates internal Wiki pages.

#### /test-agent

- **Role**: System.
- **Context**: On first install or when debugging the IDE integration.
- **Action**: Runs a logic simulation to verify that the Agent can read/write memory and access Context7 tools without hallucinating.

#### /info

- **Action**: Performs a deep diagnostic of tools and detected stack.

#### /commit

- **Role**: Git Manager.
- **Action**: Generates a Semantic Commit Message (e.g., feat(auth): add login) based on staged changes and commits them.

---

# РУКОВОДСТВО ОПЕРАТОРА (Russian)

Это документ описывает, как управлять Агентной ОС (Agent OS).

## 1. Режимы Работы

### Режим "Скорость" (Vibecoding)

Используйте, когда нужно просто писать код.

1.  **ТЗ**: /prompt "Идея".
2.  **Код**: /feature "Задача".
3.  **Полировка**: /fix -> /format.
4.  **Гит**: /commit.

### Режим "Энтерпрайз" (Компания)

Используйте для стартапов и проработки продукта.

1.  **Стратегия**: /startup (CEO).
2.  **Спецификация**: /spec (CPO).
3.  **Реализация**: /feature (CTO/Team).
4.  **Проверка**: /verify-release (CISO).
5.  **Маркетинг**: /promote (CMO).

---

## 2. СПРАВОЧНИК КОМАНД

### Бизнес (C-Suite)

- /startup — **CEO**. Анализ жизнеспособности идеи и рынка.
- /spec — **CPO**. Создание PRD и User Stories.
- /verify-release — **CISO**. Блокировка релиза при наличии уязвимостей.
- /promote — **CMO**. Генерация маркетинговых текстов.

### Разработка

- /prompt — **Архитектор**. Уточнение ТЗ.
- /feature — **Строитель**. План -> Код -> Тест. (Без галлюцинаций!).

### Качество и Инфраструктура

- /fix — **Медик**. Лечит баги и типизацию (убирает any).
- /format — **Уборщик**. Форматирует код (snake_case, табы, без комментов).
- /audit — **Шерлок**. Ищет дыры в безопасности.
- /infra — **Ops**. Настраивает K8s, Kafka, Nginx.
- /db-migrate — **DBA**. Безопасные миграции БД.

### Документация и Система

- /doc — **Писатель**. Создает Swagger, README или Wiki по коду.
- /test-agent — **Система**. Тест-драйв агента (проверка памяти и инструментов).
- /info — Диагностика стека и инструментов.
- /commit — Умный коммит.
- /summary — Отчет за сессию.