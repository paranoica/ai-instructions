# DEVOPS AND INFRASTRUCTURE STANDARDS

Activation: Glob(Dockerfile, docker-compose.yml, k8s/**/\*, nginx.conf, **/_.yaml, \*\*/_.toml)

## 1. CONTAINERIZATION (DOCKER)

- **Base Images**: Deterministic tags (`node:20-alpine3.18`). No `latest`.
- **Security**: Non-root user. No secrets in ENV or build args.
- **Structure**: Multi-stage builds. Layers ordered by cache frequency.

## 2. ORCHESTRATION (KUBERNETES)

- **Manifests**:
  - Use Helm Charts or Kustomize for environment variance.
  - Always define `resources` (requests & limits) for CPU and Memory.
  - Liveness and Readiness probes are mandatory for all services.
- **Security**:
  - Read-only root filesystem where possible.
  - No `hostPath` mounts.
  - Secrets via External Secrets Operator or Sealed Secrets.
- **Networking**:
  - Use Ingress Controllers (Nginx/Traefik).
  - Network Policies default deny.

## 3. PROXY & LOAD BALANCING (NGINX)

- **Config**:
  - Strict timeouts (`proxy_read_timeout`, `client_body_timeout`).
  - Disable server tokens (`server_tokens off`).
  - Secure headers (HSTS, X-Frame-Options).
- **Performance**: Enable Gzip/Brotli compression. Adjust `worker_connections`.

## 4. ASYNC MESSAGING (KAFKA / RABBITMQ)

- **Pattern**: Publisher/Subscriber via strictly typed Topics/Queues.
- **Reliability**:
  - Dead Letter Queues (DLQ) mandatory for failed processing.
  - Idempotent consumers (handle duplicate messages gracefully).
- **Schema**:
  - Kafka: Use Schema Registry (Avro/Protobuf).
  - RabbitMQ: Strict routing key conventions (`service.entity.event`).