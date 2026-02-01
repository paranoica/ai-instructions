# ARCHITECT SKILL PROTOCOL

## 1. PROJECT INITIALIZATION & STACK DETECTION

When invoked to analyze or initialize a project (`/info`):

1.  **Scan Filesystem**: Look for signature files (`package.json`, `go.mod`, `pubspec.yaml`, `pom.xml`, `Cargo.toml`).
2.  **Determine Tech Stack**:
    - Identify Language, Framework, Database (if evident), and Package Manager.
3.  **Update Artifact**: Write this data into `.agent/artifacts/tech_stack.md` following the JSON schema.
    - _Example Content_: `{"language": "TypeScript", "framework": "Next.js", "package_manager": "pnpm"}`.
4.  **Report**: Output a summary of the detected environment to the user.

## 2. PROMPT ENGINEERING (`/prompt`)

When the user asks to refine a task or generate a prompt:

1.  **Analyze Input**: Read the user's raw, vague request (e.g., "Make it work fast").
2.  **Contextualize**: Combine the request with the rules from `.agent/rules/` and `.agent/artifacts/tech_stack.md`.
3.  **Structure**: Generate a formal Engineering Task Description including:
    - **Context**: What is the current state?
    - **Goal**: What is the definition of done?
    - **Constraints**: Style guide, performance requirements, security boundaries.
    - **Steps**: A logical sequence of implementation.
4.  **Output**: Return the refined prompt in a code block for the user to copy or confirm.

## 3. MEMORY MANAGEMENT

- **Plan Creation**: When starting a feature, create/reset `.agent/artifacts/plan.md`.
- **ADR Recording**: If a major decision is made (e.g., "Switching from Axios to Fetch"), append a record to `.agent/artifacts/adr.md`.

## 4. MICROSERVICES & MESSAGING STRATEGY

When designing distributed systems:

1.  **Boundaries**: Define service boundaries based on Domain-Driven Design (Bounded Contexts).
2.  **Communication**:
    - Sync: REST/gRPC (Internal).
    - Async: Kafka/RabbitMQ (Eventual Consistency).
3.  **Broker Setup**:
    - Kafka: Define Topic partitions and replication factor.
    - RabbitMQ: Define Exchange type (Topic/Fanout) and DLQ policy.
4.  **Resilience**: Enforce Circuit Breaker and Retry patterns in the plan.