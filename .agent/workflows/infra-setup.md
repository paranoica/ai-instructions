# INFRASTRUCTURE SETUP WORKFLOW

1.  **Input**:
    - Ask: "Target platform? (K8s / Docker Compose)"
    - Ask: "Components needed? (Nginx, Kafka, RabbitMQ, Redis)"

2.  **Skill Activation**: Call **Ops Manager**.

3.  **Execution**:
    - **K8s**: Generate Helm Chart structure.
    - **Nginx**: Generate `nginx.conf` with security hardening.
    - **Broker**: Generate `docker-compose.yml` for local dev (Kafka/Zookeeper or RabbitMQ).

4.  **Microservices Check**:
    - If Microservices architecture detected: Call **Architect** to generate an Event Catalog (Topics/Queues definition).

5.  **Output**:
    - Files created.
    - Instructions: "Run `docker-compose up` to start infrastructure."