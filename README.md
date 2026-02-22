<p align="center">
  <img src="https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 21"/>
  <img src="https://img.shields.io/badge/Spring_Boot-3.3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot"/>
  <img src="https://img.shields.io/badge/Flutter-3.41-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter"/>
  <img src="https://img.shields.io/badge/PostgreSQL-16-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/AI--First-500x_Velocity-6C63FF?style=for-the-badge" alt="AI-First"/>
</p>

# CodeOps — AI-First Development Control Plane

**The unified, self-hosted platform that replaces your entire DevOps toolchain — purpose-built for teams where AI writes the code and humans provide architectural oversight.**

---

## The Problem

Modern engineering teams drown in tools. GitHub for source control, Jira for tracking, Postman for API testing, DBeaver for databases, Datadog for logging, HashiCorp Vault for secrets, Consul for service discovery — each excellent in isolation, none talking to each other. Every context switch is a manual, human-speed operation.

This fragmentation becomes an **existential problem** at AI-first velocity. When AI agents produce what a 50-person team builds in years — dozens of services, hundreds of endpoints, thousands of tables — in days, the tooling becomes the bottleneck.

**CodeOps eliminates that bottleneck.**

---

## What CodeOps Is

CodeOps is two things at once:

🖥️ **A software maintenance command center for human developers** — a native desktop application (macOS, Linux, Windows) providing a single interface for managing codebases, running AI-powered audits, investigating bugs, tracking debt, monitoring dependencies, testing APIs, querying databases, managing secrets, and viewing centralized logs.

🤖 **An operational control plane for AI development agents** — an MCP Gateway that gives tools like Claude Code programmatic access to the entire operational surface. Register services, look up ports, retrieve secrets, send HTTP requests, execute SQL, search logs, and read full architectural context — all without human intervention.

---

## Platform Architecture

```
┌──────────────────────────────────────────────────────────────────────────┐
│                  CodeOps-Client (Flutter Native Desktop)                  │
│                  macOS (primary) │ Linux │ Windows (future)               │
│                                                                          │
│  ┌──────────────────────────────────────────────────────────────────┐    │
│  │  v1.0: Audit · Compliance · Bugs · Tasks · Debt · Dependencies  │    │
│  │  GitHub · Jira · Personas · Directives · Health · Admin         │    │
│  └──────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐    │
│  │Registry│ │ Vault  │ │ Logger │ │Courier │ │DataLens│ │ Scribe │    │
│  │  UI    │ │  UI    │ │  UI    │ │  UI    │ │  UI    │ │  UI    │    │
│  └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘ └────────┘    │
│      └──────────┴──────────┴──────────┴──────────┘                      │
│                         MCP Dashboard UI                                 │
└──────┬──────────┬──────────┬──────────┬──────────┬──────────┬───────────┘
       │          │          │          │          │          │
  ┌────▼────┐ ┌───▼────┐ ┌──▼─────┐ ┌──▼─────┐ ┌──▼─────┐ ┌▼───────────┐
  │Registry │ │ Vault  │ │ Logger │ │Courier │ │DataLens│ │MCP Gateway │
  │ :8096   │ │ :8097  │ │ :8098  │ │ :8099  │ │ :8100  │ │ :8101      │
  └─────────┘ └────────┘ └────────┘ └────────┘ └────────┘ └────────────┘
       │          │          │          │          │          │
       └──────────┴──────────┴──────────┴────┬─────┴──────────┘
                                             │
                                      ┌──────▼──────┐
                                      │  CodeOps    │
                                      │  Server     │
                                      │  :8095      │
                                      └─────────────┘
                                             ▲
                                             │ MCP Protocol
                                       ┌─────┴─────┐
                                       │ Claude Code│
                                       │ AI Agents  │
                                       └────────────┘
```

---

## Services

### Core Platform (v1.0 — Complete & Running)

| Repository | Description | Status |
|:--|:--|:--|
| **CodeOps-Server** | Java 21 / Spring Boot backend — 17 controllers, 28 entities, full RBAC, MFA, JWT auth | ✅ Complete |
| **CodeOps-Client** | Flutter native desktop app — 193 files, 50K+ LOC, 2,007 tests, 100% DartDoc | ✅ Complete |

### Control Plane Services (Building Now)

| Repository | Replaces | Port | Description |
|:--|:--|:--|:--|
| **CodeOps-Registry** | Consul + service catalogs | 8096 | Service catalog, port allocation, dependency mapping, topology visualization, config generation |
| **CodeOps-Vault** | HashiCorp Vault | 8097 | Encrypted secret storage, versioning, rotation policies, transit encryption, access policies |
| **CodeOps-Logger** | Datadog / Splunk / ELK | 8098 | Centralized log ingestion, structured queries, traps & alerts, metrics, trace correlation |
| **CodeOps-Courier** | Postman Enterprise | 8099 | Full API testing — all HTTP methods, GraphQL, scripting, collection runner, code generation |
| **CodeOps-DataLens** | DBeaver / pgAdmin / DataGrip | 8100 | Multi-database management, SQL editor, ER diagrams, data editor, import/export |
| **CodeOps-MCP** | *No equivalent exists* | 8101 | MCP Gateway — AI agents get full ecosystem context, session writeback, cross-project coordination |

### Shared Components

| Repository | Description |
|:--|:--|
| **Scribe** | Shared code editor widget (Flutter) — syntax highlighting for 30+ languages, Markdown preview, diff editor |

---

## What Makes CodeOps Different

### 🔗 Deep Integration, Not Loose Coupling
Register a service → ports are allocated → database credentials generated → logging pipeline configured → API test collection created → AI agents have full context. Automatically. Every component is aware of every other component.

### 🤖 MCP Gateway — The AI Multiplier
Claude Code connects once and receives the complete, current context for any project: team conventions, architecture docs, audit results, port mappings, dependencies, secrets, and session history. No manual context assembly. No stale files. Every AI session starts with perfect information.

### 🔄 The Writeback Cycle
AI sessions write back what changed — commits, endpoints modified, coverage numbers. The next session starts from the new state. The system of record is always current because it's the database, not files in repos.

### 🔍 AI-Powered Quality Assurance
Up to 12 specialized AI agents — security, code quality, build health, API contracts, test coverage, UI/UX, documentation, performance, architecture, and more — analyze codebases concurrently. **Vera**, the orchestrator, deduplicates findings and computes composite health scores.

### 🐛 Jira-Driven Bug Investigation
Enter a ticket key → CodeOps fetches full ticket context → AI agents investigate the codebase → root cause analysis with fix tasks generated as ready-to-execute Claude Code prompts. Bug triage in minutes, not hours.

---

## SaaS Cost Replacement

| CodeOps Service | Replaces | Annual Cost Eliminated |
|:--|:--|--:|
| Registry | Consul + custom catalogs | $50K – $200K |
| Vault | HashiCorp Vault | $100K – $500K |
| Logger | Datadog / Splunk / ELK | $200K – $1M+ |
| Courier | Postman (Team/Enterprise) | $50K – $200K |
| DataLens | DBeaver Pro + pgAdmin + DataGrip | $20K – $100K |
| MCP Gateway | No market equivalent | Novel capability |
| **Total** | | **$420K – $2M+/year** |

---

## Technology Stack

**Backend** — Java 21, Spring Boot 3.3.0, PostgreSQL 16, Redis 7, Kafka (Confluent 7.5), Hibernate, JWT (jjwt 0.12.6), MapStruct, Lombok, Testcontainers, Logback (structured JSON in prod)

**Frontend** — Flutter 3.41 / Dart 3.11, Riverpod, GoRouter, Dio, Drift (SQLite), Material 3 dark theme, fl_chart, flutter_markdown

**Infrastructure** — Docker Compose (dev), AWS ECS Fargate (prod), per-service PostgreSQL instances, shared JWT authentication across all services

**Security** — AES-256-GCM encryption at rest, RBAC (OWNER/ADMIN/MEMBER/VIEWER), MFA (TOTP + email), X-Correlation-ID request tracing, rate limiting, OS keychain token storage

---

## Development Methodology

CodeOps is built using **AI-first development** — AI writes 100% of production code while humans provide architectural oversight. This methodology achieves development velocities approaching **500x traditional speed**.

The existing v1.0 platform (CodeOps-Server + CodeOps-Client) was built from scratch starting December 28, 2025, with the entire system operational in approximately 3 days. The desktop client ships with 50,000+ lines of code, 2,007 tests, and 100% documentation coverage.

Every commit includes complete implementations — no TODOs, no stubs, no partial features. Code ships with full test coverage and documentation in the same pass.

---

## Local Development

```bash
# Start infrastructure
docker compose -f docker-compose.databases.yml up -d
# → PG:5434-5440 | Redis:6380 | Kafka:9094 | Zookeeper:2182

# Start backend services
cd CodeOps-Server   && mvn spring-boot:run    # :8095
cd CodeOps-Registry && mvn spring-boot:run    # :8096
cd CodeOps-Vault    && mvn spring-boot:run    # :8097
cd CodeOps-Logger   && mvn spring-boot:run    # :8098
cd CodeOps-Courier  && mvn spring-boot:run    # :8099
cd CodeOps-DataLens && mvn spring-boot:run    # :8100
cd CodeOps-MCP      && mvn spring-boot:run    # :8101

# Start Flutter desktop client
cd CodeOps-Client && flutter run -d macos
```

---

<p align="center">
  <sub>Built with AI-first methodology · Designed for the teams building the future</sub>
</p>
