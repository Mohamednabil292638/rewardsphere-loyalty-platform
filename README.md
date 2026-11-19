# RewardSphere — Enterprise Loyalty & Rewards Platform

RewardSphere is a Java-based backend project for managing customer loyalty accounts, reward points, and reward redemption workflows. It is being developed with an emphasis on reliable transaction processing, clear service boundaries, and event-driven integration.

> **Project status:** Initial repository setup. Features and technology integrations will be documented as they are implemented and tested.

## Project Goals

- Manage customer loyalty accounts and point balances.
- Record point credits and debits with an auditable ledger.
- Support reward catalogue and redemption workflows.
- Protect operations against duplicate requests and concurrent redemptions.
- Explore asynchronous integration using Kafka.
- Add automated tests, containerized local development, and CI.

## Planned Technology Stack

| Area | Planned technology |
|---|---|
| Language | Java 21 |
| Backend | Spring Boot |
| API | REST, OpenAPI |
| Persistence | PostgreSQL, Spring Data JPA |
| Messaging | Apache Kafka |
| Cache | Redis |
| Security | Spring Security, JWT |
| Migrations | Flyway |
| Testing | JUnit 5, Mockito, Testcontainers |
| Containers | Docker, Docker Compose |
| CI | GitHub Actions |

*The table describes the intended stack, not a claim that every component is already implemented.*

## Planned Architecture

The implementation will be divided into well-defined services as the domain grows:

- **Identity Service** — customer identity and authentication.
- **Loyalty Service** — loyalty accounts, point earning, balance, and ledger.
- **Rewards Service** — reward catalogue and eligibility.
- **Redemption Service** — redemption orchestration and state management.
- **Notification Service** — asynchronous customer notifications.

Service boundaries will be validated against actual business and data ownership needs during implementation.

## Core Engineering Concerns

1. **Ledger integrity:** preserve an auditable record of every points movement.
2. **Idempotency:** prevent duplicate processing when clients retry requests.
3. **Concurrency:** ensure simultaneous redemption requests cannot overspend a balance.
4. **Reliable events:** use an outbox-based approach where database changes and event publication must remain consistent.
5. **Resilience:** define retry, failure, and dead-letter handling for asynchronous workflows.
6. **Verification:** cover business rules with unit and integration tests.

## Getting Started

The application setup is currently in progress. Run instructions, environment variables, database configuration, and API examples will be added after the first runnable service is committed.

## Repository Structure (Planned)

```text
rewardsphere-loyalty-platform/
├── docs/
│   ├── architecture.md
│   ├── database-design.md
│   └── api-specification.md
├── services/
│   ├── identity-service/
│   ├── loyalty-service/
│   ├── rewards-service/
│   ├── redemption-service/
│   └── notification-service/
├── infrastructure/
├── .github/
│   └── workflows/
└── README.md
```

## Development Roadmap

- [ ] Establish Java 21 and Spring Boot project foundation.
- [ ] Configure PostgreSQL and database migrations.
- [ ] Implement the loyalty account and points ledger.
- [ ] Add earn and redeem APIs with validation and error handling.
- [ ] Add idempotency and concurrency protection.
- [ ] Add Kafka event publishing and consumption.
- [ ] Implement reliable event delivery and failure handling.
- [ ] Add integration tests and Docker Compose.
- [ ] Add CI checks and operational documentation.

## Engineering Principles

- Keep business rules in the domain/application layer, not in controllers.
- Validate inputs and return consistent API errors.
- Keep secrets and environment-specific configuration out of Git.
- Document only behavior that exists and can be demonstrated.
- Prefer tested, incremental delivery over a large unverified scaffold.

## License

A license has not yet been selected. Until one is added, standard copyright restrictions apply.
