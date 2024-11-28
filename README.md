# Microsysarch  - Secure, Scalable, and Observable Microservice Architecture

This project is structured as a demonstration of a secure and flexible microservice architecture. With token-based authorization, route management, and monitoring tools, these components integrate important concepts for a scalable and user-friendly system.

The whole demonstrator is based on docker compose with several configuration files for individual architecture members.

The system is built around the following components:

- Reverse Proxy (NGINX with TLS and DoS protection)
- Kong API Gateway (Authorization checks, routing, and rate limiting)
- Keycloak (User and access management, token issuance)
- Services (examples of routed microservices)
- Fluentd (Centralized log management)
- OpenSearch (Searchable logs and metrics)
- Prometheus & Grafana (Metrics and monitoring)

Below is a high-level representation of the architecture demonstrating the flow of traffic and the integration of components.

```plaintext
Client 
  |
  v
Reverse Proxy (TLS termination, DoS protection)
  |
  v
API Gateway (Authorization, Routing, Rate Limiting)
  |
  +--> Service A
  |
  +--> Service B
  |
  +--> Service C
  |
  v
Monitoring Stack:
  +--> Fluentd -> OpenSearch -> OpenSearch Dashboards
  +--> Prometheus -> Grafana
  +--> Tracing -> Jaeger/OpenTelemetry
  |
Keycloak (User Management, Token Issuance)
```

## Features and Components

* Reverse Proxy:
  - TLS termination
  - DoS and other standard security measures
  - Routes traffic to the API Gateway

* Kong API Gateway:
  - Authenticates API calls using token-based authentication (JWT)
  - Performs validity checks for expired, malformed, or unauthorized requests
  - Rate limiting and IP-based restrictions

* Keycloak:
  - User management
  - Token issuance and verification at request level
  - Roles and permission management

* Prometheus & Grafana:
  - Collects and visualizes metrics from various components
  - Monitors system performance and latencies

* Fluentd:
  - Centralizes logs from all components
  - Sends them to OpenSearch for querying and visualization
  - Manages index lifecycles to optimize log data storage

* OpenSearch:
  - Searchable and queryable logs
  - Integrates with Fluentd and other collectors

**Goal of this project:** Test and learn to set up a secure, scalable, and observable microservice architecture.

**How to Run**

- copy this repository to your local machine
- decode it using `base64 -d filename.md`.
- run `docker-compose up -d`
