# AGENT OS: INTERNAL PROCESS FLOWS

This document visualizes the logic chains for every system command. It explains how the Agent OS orchestrates memory, tools, and skills to execute tasks without hallucinating.

---

## 1. STRATEGY & PRODUCT CHAINS (Enterprise Mode)

### /startup (CEO Strategy Session)

**Goal**: Validate business viability before writing code.
`User Input` -> **Brain** (Activates CEO Skill) -> **Context7** (Competitor Research) -> **CEO** (Critique & SWOT Analysis) -> **Artifact Write** (`.agent/company/STRATEGY.md`) -> **Output** (Go/No-Go Recommendation).

### /spec (CPO Requirements)

**Goal**: Convert abstract strategy into engineering tasks.
`STRATEGY.md` -> **Brain** (Activates CPO Skill) -> **CPO** (Draft User Stories) -> **CPO** (Define Acceptance Criteria) -> **Artifact Write** (`.agent/company/PRD.md`) -> **Output** (Ready for Engineering).

### /verify-release (CISO Security Gate)

**Goal**: Prevent dangerous deployments.
**Brain** (Activates CISO Skill) -> **Sherlock** (Deep Code Scan) -> **Ops Manager** (Container/Infra Scan) -> **CISO** (Compliance Check) -> **Decision** (VETO if Critical Issues found OR APPROVE) -> **Output** (Verification Report).

### /promote (CMO Marketing)

**Goal**: Translate code into public announcements.
`task.md` (Completed Items) -> **Brain** (Activates CMO Skill) -> **CMO** (Translate "Refactor Auth" to "New Secure Login") -> **Output** (Draft Tweet / Blog Post / Release Notes).

---

## 2. DEVELOPMENT CHAINS (Standard Mode)

### /prompt (Architectural Spec)

**Goal**: Refine a vague idea into a technical specification.
`User Idea` -> **Brain** (Activates Architect) -> **Memory Read** (`tech_stack.md`) -> **Architect** (Align idea with Stack & Conventions) -> **Output** (Detailed Engineering Prompt block).

### /feature (The Builder Loop)

**Goal**: Implement a feature with strict anti-hallucination protocols.

1. **Research**: `User Request` -> **Architect** -> **Context7** (Fetch Library Docs/Versions) -> **Memory Write** (`plan.md`).
2. **Approval**: **System** -> User Confirmation -> **Start**.
3. **Execution**: **Builder** -> **Memory Read** (`conventions.md`) -> **Write Code** -> **Janitor** (Auto-Format) -> **Verify** (Build/Test).
4. **Update**: **System** -> **Memory Write** (`task.md` mark step complete).

---

## 3. MAINTENANCE & QUALITY CHAINS

### /fix (The Medic Loop)

**Goal**: Repair bugs and eliminate "any" types.
`Error Log / File` -> **Brain** (Activates Medic) -> **Context7** (Lookup Library Types) -> **Medic** (Generate Strict Interface) -> **Apply Fix** -> **Verify** (Run Compiler) -> **Result** (Success or Retry).

### /format (The Janitor Pipeline)

**Goal**: Enforce coding standards.
`Target File` -> **Brain** (Activates Janitor) -> **Tool Check** (Prettier/ESLint?) -> **Step A** (Run Tools) -> **Step B** (Manual Polish: Remove Comments, Snake Case Variables, Tab Indentation) -> **Save**.

### /audit (Sherlock Scan)

**Goal**: Non-invasive security and architecture review.
`Codebase` -> **Brain** (Activates Sherlock) -> **Pattern Match** (OWASP Top 10) -> **Arch Check** (Violations of `rules/*.md`) -> **Output** (Read-Only Markdown Report).

---

## 4. INFRASTRUCTURE CHAINS (DevOps)

### /infra (Scaffolding)

**Goal**: Setup environment.
`User Choice` (e.g., Kafka) -> **Brain** (Activates Ops Manager) -> **Memory Read** (`tech_stack.md`) -> **Ops** (Generate Docker Compose / K8s Helm Charts) -> **Output** (Config Files).

### /db-migrate (DBA Protocol)

**Goal**: Safe database evolution.
`User Request` -> **Brain** (Activates DBA) -> **Context7** (Read current Schema) -> **DBA** (Draft Change) -> **Safety Check** (Is data deletion likely?) -> **Generate Migration Script** -> **Verify** (SQL Check).

### /docker-build (Container Ops)

**Goal**: Production-ready artifacts.
`Dockerfile` -> **Ops** (Lint Config) -> **Build Command** -> **Ops** (Analyze Layer Size & Cache usage) -> **Output** (Optimization Suggestions).

---

## 5. SYSTEM & DOCUMENTATION CHAINS

### /doc (Tech Writer)

**Goal**: Auto-generate documentation.
`Codebase` -> **Brain** (Activates Tech Writer) -> **Analysis** (Extract Routes/DTOs) -> **Generation** (Swagger JSON or README.md) -> **Save**.

### /test-agent (Self-Diagnostic)

**Goal**: Verify IDE integration.
**System** -> **Kernel Ping** (Check Context7) -> **Memory Test** (Write/Read Artifact) -> **Logic Sim** (Architect -> Builder Handshake) -> **Output** (Health Status).

### /info (Initialization)

**Goal**: Detect environment.
**System** -> **File Scan** (`package.json`, `go.mod`, etc.) -> **Rule Match** (Activate Web/Mobile/System Rules) -> **Memory Write** (`tech_stack.md`) -> **Output** (Stack Report).

### /commit (Git Manager)

**Goal**: Standardize history.
`git diff --staged` -> **Brain** (Activates Git Manager) -> **Analysis** (Determine feat/fix/chore) -> **Formatting** (Truncate to 72 chars, lowercase) -> **Output** (Commit Command).

---

# ВНУТРЕННИЕ ПРОЦЕССЫ AGENT OS (Russian)

Этот документ описывает логические цепочки выполнения команд. Он показывает, как данные передаются между Пользователем, Мозгом, Навыками и Памятью.

## 1. СТРАТЕГИЯ И ПРОДУКТ (Enterprise Mode)

### /startup (Стратегия CEO)

`Ввод пользователя` -> **Мозг** (CEO Skill) -> **Context7** (Поиск конкурентов) -> **CEO** (Критика и SWOT) -> **Запись в память** (`.agent/company/STRATEGY.md`) -> **Вывод** (Рекомендация).

### /spec (Требования CPO)

`STRATEGY.md` -> **Мозг** (CPO Skill) -> **CPO** (User Stories) -> **CPO** (Критерии приемки) -> **Запись в память** (`.agent/company/PRD.md`) -> **Вывод** (Готово к разработке).

### /verify-release (Контроль CISO)

**Мозг** (CISO Skill) -> **Sherlock** (Скан кода) -> **Ops Manager** (Скан контейнеров) -> **CISO** (Проверка политик) -> **Решение** (VETO или APPROVE) -> **Вывод** (Отчет).

### /promote (Маркетинг CMO)

`task.md` (Завершенные задачи) -> **Мозг** (CMO Skill) -> **CMO** (Перевод с технического на человеческий) -> **Вывод** (Черновик Твита / Поста / Релиз ноутс).

---

## 2. РАЗРАБОТКА (Standard Mode)

### /prompt (Архитектурное ТЗ)

`Идея` -> **Мозг** (Architect) -> **Чтение памяти** (`tech_stack.md`) -> **Architect** (Генерация промпта с учетом стека) -> **Вывод** (Блок инженерного промпта).

### /feature (Цикл Строителя)

1. **Ресерч**: `Запрос` -> **Architect** -> **Context7** (Проверка версий библиотек) -> **Запись** (`plan.md`).
2. **Утверждение**: **System** -> Подтверждение юзера -> **Старт**.
3. **Исполнение**: **Builder** -> **Чтение правил** (`conventions.md`) -> **Код** -> **Janitor** (Авто-формат) -> **Проверка** (Тесты).
4. **Обновление**: **System** -> **Запись** (`task.md`).

---

## 3. КАЧЕСТВО И ПОДДЕРЖКА

### /fix (Цикл Медика)

`Ошибка / Файл` -> **Мозг** (Medic) -> **Context7** (Поиск типов) -> **Medic** (Создание интерфейса) -> **Фикс** -> **Проверка** (Компилятор) -> **Результат**.

### /format (Конвейер Уборщика)

`Файл` -> **Мозг** (Janitor) -> **Проверка тулзов** (Prettier?) -> **Шаг A** (Запуск тулзов) -> **Шаг B** (Ручная чистка: удаление комментов, snake_case, табы) -> **Сохранение**.

### /audit (Сканер Шерлока)

`Код` -> **Мозг** (Sherlock) -> **Паттерны** (OWASP Top 10) -> **Архитектура** (Нарушения `rules/*.md`) -> **Вывод** (Отчет без изменений кода).

---

## 4. ИНФРАСТРУКТУРА (DevOps)

### /infra (Скелет)

`Выбор юзера` (напр. Kafka) -> **Мозг** (Ops Manager) -> **Чтение памяти** (`tech_stack.md`) -> **Ops** (Генерация Docker Compose / Helm) -> **Вывод** (Файлы конфигов).

### /db-migrate (Протокол DBA)

`Запрос` -> **Мозг** (DBA) -> **Context7** (Чтение схемы БД) -> **DBA** (Проект изменений) -> **Проверка безопасности** (Удаляются ли данные?) -> **Генерация миграции** -> **Проверка** (SQL).

### /docker-build (Сборка)

`Dockerfile` -> **Ops** (Линтер) -> **Билд** -> **Ops** (Анализ слоев и кэша) -> **Вывод** (Советы по оптимизации).

---

## 5. СИСТЕМА И ДОКУМЕНТАЦИЯ

### /doc (Технический писатель)

`Код` -> **Мозг** (Tech Writer) -> **Анализ** (Роуты/DTO) -> **Генерация** (Swagger JSON или README.md) -> **Сохранение**.

### /test-agent (Самодиагностика)

**System** -> **Пинг Ядра** (Context7) -> **Тест Памяти** (Чтение/Запись) -> **Симуляция** (Связка Architect -> Builder) -> **Вывод** (Статус здоровья).

### /info (Инициализация)

**System** -> **Скан файлов** (`package.json`, `go.mod`) -> **Активация Правил** (Web/System) -> **Запись** (`tech_stack.md`) -> **Вывод**.

### /commit (Git Менеджер)

`git diff --staged` -> **Мозг** (Git Manager) -> **Анализ** (feat/fix/chore) -> **Форматирование** (72 символа, lowercase) -> **Вывод** (Команда коммита).