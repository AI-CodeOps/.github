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

## Why CodeOps Exists

CodeOps was born from a fundamental realization: when AI agents write 100% of production code, the biggest bottleneck isn't code generation — it's **context**.

Every developer on every team operates on an island. They have their own local copies of architecture documents, their own CONVENTIONS.md files, their own understanding of what ports are allocated, what secrets are needed, and what the team's coding standards look like today. When Developer A updates a convention on Monday, Developer B's AI session on Tuesday is still working from the old version. When a new service gets registered at 3pm, the rest of the team's local configuration files are stale by 3:01pm. Multiply this across a dozen developers, thirty services, and hundreds of AI sessions per week, and you get an ecosystem held together by tribal knowledge, Slack messages, and hope.

This is the environment island problem, and at traditional development speed, it's manageable. Teams hold standups, write Confluence pages, and trust that drift will be caught in code review. But at AI-first velocity — where a single developer with AI agents produces what used to require a 50-person team — the islands don't just drift. They diverge catastrophically, because the volume of change outpaces every human coordination mechanism.

CodeOps solves this by putting a **centralized cloud database** at the center of everything. Personas, directives, coding conventions, architecture documents, audit results, service registrations, port allocations, secret references, session histories — all of it lives in one authoritative source, served fresh to every developer and every AI agent on every session. When a team lead updates a coding standard, it propagates instantly to every project across the entire organization. When a new service is registered, every other tool in the platform knows about it immediately. There is no sync step, no manual propagation, no "make sure you pull the latest CONVENTIONS.md." The database is the truth, and everything reads from it in real time.

The **MCP Gateway** is what makes this centralized truth actionable for AI. When Claude Code connects to CodeOps, it calls a single initialization function and receives everything it needs: the team's AI persona (behavioral identity, coding standards, testing requirements), the canonical conventions, all project documents (architecture specs, audit results, OpenAPI contracts), the full ecosystem context from the Registry (ports, dependencies, routes, related services), secret references from the Vault, active team directives, and a summary of what happened in recent sessions — including who changed what and which commits were involved. The AI doesn't start from a stale file in a repo. It starts from the current state of the world, assembled automatically from the single source of truth.

When the session ends, the AI writes back what it did — commits, files changed, endpoints modified, tests added, coverage numbers. CodeOps stores this as a session record and updates the project state so the next session, whether it's the same developer or a teammate on the other side of the building, starts from the new reality. This **writeback-and-refresh cycle** is what eliminates context staleness permanently. The system of record isn't a file that goes stale after every commit. It's a living database, updated by every session, served fresh to every subsequent session.

This is not an incremental improvement to how teams use developer tools. It's a fundamentally new workflow where the platform itself maintains the shared context that makes every AI session — and every human decision — informed by the complete, current state of the entire ecosystem.

---

## What You Can Do With CodeOps

CodeOps is both a **software maintenance command center for human developers** and an **operational control plane for AI agents**. Here's the full picture of what it enables:

### Eliminate Developer Environment Islands
Every developer and every AI session reads from the same centralized source of truth. Update a coding convention once and it's instantly active across every project, every developer, and every AI session in the organization. No more "did you pull the latest?" No more conventions drifting between repos. No more onboarding a new developer by pointing them at six different wikis and hoping the information is current.

### Give AI Agents Perfect Context — Every Time
Today, starting a Claude Code session means manually assembling context: copy the CONVENTIONS.md, paste the architecture doc, reference the audit results, look up ports, find credentials, and hope it's all current. CodeOps eliminates this entirely. AI agents connect via MCP and receive the complete, current context for any project in one call. The quality of every AI session goes up because the context is always perfect, always current, and always complete.

### Manage Shared AI Personas and Directives
Personas define how each AI agent behaves — what it focuses on, how it calibrates severity, what format it outputs. Directives are reusable context documents (coding standards, project-specific rules, compliance requirements) that get injected into every AI agent's prompt. Both are stored centrally, versioned, and shared across the team. A "Java Coding Standards" directive that specifies constructor injection patterns and PreAuthorize conventions applies to every project and every AI session automatically. Teams can create custom personas that override built-in defaults, scope directives to specific projects, and test them against sample code before deploying.

### Run AI-Powered Quality Audits
Dispatch up to 12 specialized AI agents — covering security, code quality, build health, completeness, API contracts, test coverage, UI/UX, documentation, database integrity, performance, dependency health, and architecture — against any codebase. An orchestrator named **Vera** manages the dispatch, deduplicates findings, and computes a composite health score. What would take a human team days or weeks is delivered in minutes. Findings are stored in the cloud, queryable, filterable, and trackable over time. Schedule recurring audits daily, weekly, or triggered by commits.

### Investigate Bugs in Minutes, Not Hours
Enter a Jira ticket key and CodeOps fetches the full ticket context — description, comments, attachments, linked issues. It identifies the relevant codebase, dispatches AI agents armed with the Jira context, and produces a root cause analysis with impact assessment and a set of fix tasks. Each fix task is a complete, ready-to-execute Claude Code prompt. Post the RCA back to Jira, create sub-tasks, assign them, and track them through resolution — all without leaving CodeOps.

### Generate Ready-to-Execute Remediation Tasks
Every audit, compliance check, and bug investigation produces findings. CodeOps converts those findings into ordered, grouped remediation tasks formatted as complete Claude Code prompts following the team's methodology. Each task contains the finding description, file paths, relevant code patterns, expected behavior, coding conventions, and explicit instructions to compile, test, commit, and push. Export as Markdown files, ZIP archives, or push directly to Jira with all fields pre-populated. The human reviews and approves. The AI executes. The next audit confirms the fixes landed.

### Validate Specification Compliance
Compare actual implementations against formal specifications — OpenAPI contracts, design documents, architecture decision records. Upload specs and the AI agents examine the codebase for gaps: missing endpoints, incorrect response shapes, unimplemented business rules, UI elements that don't match the design. The output is a compliance matrix showing which requirements are met, partially met, or missing, along with a compliance score and gap analysis.

### Track and Trend Technical Debt
Identify, categorize, and trend technical debt across five dimensions: architecture, code, test, dependency, and documentation. Each item includes severity, effort estimate, and business impact rating. Track whether debt is growing or shrinking, which categories are most problematic, and which items have been open the longest. Convert any debt item into a remediation task and push it to Jira.

### Catalog Every Service in Your Ecosystem
The Registry is the single source of truth for every service, port, database, route, and cloud resource. Register a new service and it automatically allocates ports, generates a complete identity kit (Docker container names, network names, database names, API route prefixes), maps dependencies, and makes all of that context available to every other tool in the platform. Generate docker-compose files, Spring Boot configs, and Claude Code prompt headers directly from Registry data. Change a port allocation once and every generated configuration updates to match.

### Secure Secrets From Day One
Encrypted secret storage with hierarchical paths, automatic versioning (secrets are never overwritten), rotation policies, access control with deny-overrides-allow semantics, and transit encryption as a service. When the Registry registers a new service that needs a database, the Vault generates credentials automatically. No more plaintext .env files scattered across repositories.

### Centralize Logs, Metrics, and Traces
Ingest logs via HTTP push and Kafka, search with structured queries and full-text search, and set traps that fire alerts on pattern matches, frequency thresholds, or absence detection. Collect metrics (counters, gauges, histograms, timers) with automatic Spring Actuator integration. Assemble cross-service request traces via X-Correlation-ID propagation, visualized as waterfall timelines showing exactly how a request flowed through the ecosystem.

### Test Every API From One Place
A full Postman replacement — all HTTP methods, GraphQL with schema introspection, pre-request and post-response scripting, collection runner with iterations and data files, code generation in 10+ languages. The critical difference: Courier auto-discovers every service from the Registry, fetches its OpenAPI spec, and generates a complete test collection with one click. When APIs change, regenerate and the collection is current.

### Manage Every Database From One Place
Multi-database support (PostgreSQL, MySQL, MariaDB, SQLite, SQL Server, Oracle, H2) with SQL editor, autocomplete from metadata, EXPLAIN visualization, inline data editing, ER diagram generation, import/export, and SSH tunnel support. Credentials come from the Vault, never stored locally. All SQL executes server-side — database credentials never reach the client.

### Coordinate AI Sessions Across the Team
A team-wide activity feed shows what every AI session across every project produced, enabling coordination without meetings. Cross-project impact detection operates at the speed the work happens, replacing standups and sprint planning as the coordination mechanism for AI-first teams.

### Manage Source Control Without Leaving CodeOps
A complete GitHub Desktop equivalent built into the native app. Browse organizations and repos, clone with progress tracking, switch and create branches, commit, push, pull, view diffs with syntax highlighting, manage stashes, create and merge pull requests, view CI status, and browse commit history.

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

## The Integration Advantage

CodeOps is not a collection of tool clones. It is a deeply connected platform where every component is aware of every other component:

**Register a service** → ports are allocated from configurable ranges → database credentials are generated in the Vault → logging pipeline is configured in the Logger → an API test collection is generated in Courier → the full context is available to any AI agent via MCP. Automatically, instantly, with zero manual wiring.

**Update a convention** → every developer's next AI session reflects the change → every project across the organization follows the new standard → no propagation delay, no stale copies, no "which version of CONVENTIONS.md is current?"

**Run an audit** → findings are stored centrally → remediation tasks are generated as Claude Code prompts → tasks can be pushed to Jira → AI executes the fixes → the next audit confirms they landed. The loop closes itself.

**An AI session completes** → commit hashes, files changed, and test coverage are written back → the project's state is updated → the next session (any developer, any project) starts from the current state → the team activity feed shows what happened without requiring a standup.

No combination of separate SaaS products provides this integrated view, because they were never designed to share context with each other or with AI agents.

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

CodeOps is built using **AI-first
