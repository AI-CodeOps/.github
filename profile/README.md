<p align="center">
  <img src="https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 21"/>
  <img src="https://img.shields.io/badge/Spring_Boot-3.3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot"/>
  <img src="https://img.shields.io/badge/Flutter-3.41-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter"/>
  <img src="https://img.shields.io/badge/PostgreSQL-16-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/AI--First-500x_Velocity-6C63FF?style=for-the-badge" alt="AI-First"/>
</p>

# CodeOps — AI-First Development Control Plane (v1.0 Complete)

---

# Part I — Product Vision & Functional Overview

---

## The Problem CodeOps Solves

Modern software engineering is drowning in tools. A typical enterprise team pays for GitHub or Azure DevOps for source control, Jira for issue tracking, Postman for API testing, DBeaver or DataGrip for database management, Datadog or Splunk for logging and monitoring, HashiCorp Vault for secrets management, Consul for service discovery, and an assortment of one-off scripts and spreadsheets to keep track of which service runs on which port, which database belongs to which application, and which credentials unlock which environment. Each of these tools is excellent in isolation, but none of them talk to each other in any meaningful way. A developer working on a payment service has to check Consul to find its port, look up its secrets in Vault, tail logs in Datadog, test endpoints in Postman, inspect the database in DBeaver, and cross-reference all of it with Jira tickets and GitHub pull requests. The cognitive overhead is enormous, and it scales linearly with the number of services in the ecosystem.

This fragmentation becomes an existential problem when teams adopt AI-first development. When AI agents like Claude Code write one hundred percent of production code at speeds approaching five hundred times traditional developer velocity, the output looks like what a large engineering organization produces — dozens of services, hundreds of endpoints, thousands of database tables, complex dependency graphs — except it's built in days, not years, and by a team of one or two people rather than fifty. Traditional tooling was designed for traditional pace. At AI-first speed, the tooling becomes the bottleneck, because every context switch between tools is a manual, human-speed operation that the AI cannot perform autonomously.

CodeOps exists to eliminate that bottleneck. It is a unified, self-hosted platform that replaces the entire constellation of expensive SaaS products with a single integrated system, purpose-built for AI-first development teams. It is not a loose collection of clones. It is a deeply connected platform where every component is aware of every other component, where registering a service automatically allocates its ports, generates its database credentials, configures its logging pipeline, creates an API test collection, and makes all of that context instantly available to any AI agent that connects via the Model Context Protocol. No other product in the market does this, because no other product was designed from the ground up for a world where AI writes the code and humans provide architectural oversight.

## What CodeOps Is

CodeOps is two things at once: a software maintenance command center for human developers, and an operational control plane for AI development agents.

For human developers, CodeOps is a native desktop application — built in Flutter for macOS, Linux, and Windows — that provides a single interface for managing codebases, running AI-powered quality audits, investigating bugs, tracking technical debt, monitoring dependency health, testing APIs, querying databases, managing secrets, and viewing centralized logs. It integrates directly with GitHub for source control and Jira for issue tracking, so developers never need to leave CodeOps to perform any routine engineering task.

For AI agents, CodeOps exposes the same capabilities through an MCP Gateway — a machine-readable interface that allows tools like Claude Code to connect once and gain programmatic access to the entire operational surface. The AI can register services, look up ports, retrieve secrets, send HTTP requests, execute SQL queries, search logs, and read the full architectural context of any project, all without human intervention. When the AI finishes a session, it writes back what changed — commit hashes, updated API specs, new test coverage numbers — so the next session, whether initiated by the same developer or a teammate, starts from the current state rather than stale files.

This dual nature is what makes CodeOps fundamentally different from the products it replaces. Vault stores secrets for human consumption via a web UI. CodeOps-Vault stores secrets for both human consumption via the desktop app and AI consumption via the MCP Gateway. The same is true for every other component: the Registry, the Logger, Courier, DataLens, and Scribe all serve both audiences through a single, unified backend.

## How CodeOps Works — The Complete Picture

### Quality Assurance & Codebase Health

At its core, CodeOps is a QA platform. The existing v1.0 system dispatches up to twelve specialized AI agents — covering security, code quality, build health, completeness, API contracts, test coverage, UI/UX, documentation, database integrity, performance, dependency health, and architecture — as Claude Code subprocesses against any codebase. An orchestrator persona called Vera manages the dispatch, deduplicates findings across agents, computes a composite health score, and produces an executive summary.

The audit workflow begins when a developer selects a project and its repository, configures which agents to run, and launches the analysis. CodeOps clones or pulls the repository locally, assembles each agent's prompt from a layered system of personas and directives (built-in defaults overridden by team customizations and augmented by project-specific context), and spawns each agent as an isolated subprocess. The agents analyze the codebase concurrently — up to six at a time, configurable — and produce structured Markdown reports following a standardized format. As each agent completes, CodeOps parses its report into structured findings with severity levels, file paths, line numbers, recommendations, effort estimates, and supporting evidence. Vera then consolidates everything, removes duplicate findings that multiple agents may have flagged independently, and calculates the final health score.

The result is a comprehensive, multi-perspective audit of the codebase that would take a human team days or weeks to produce, delivered in minutes. Every finding is stored in the cloud service, queryable, filterable by severity and agent type and status, and trackable over time. Teams can mark findings as acknowledged, false positive, or fixed, and the system tracks who changed each status and when. Health scores are stored as time-series snapshots, allowing teams to visualize quality trends across weeks and months, set threshold alerts that fire when health drops below a configurable level, and schedule recurring audits on a daily, weekly, or on-commit basis.

### Bug Investigation

CodeOps provides a Jira-driven bug investigation workflow that is unlike anything available in traditional tools. A developer enters a Jira ticket key — say, PAY-456, "Payment fails for amounts over ten thousand dollars" — and CodeOps fetches the full ticket details, comments, attachments, and linked issues from Jira. It identifies the relevant codebase from the project's GitHub mapping, then dispatches AI agents to investigate the bug specifically, armed with the Jira context. The result is a root cause analysis report with an impact assessment and a set of fix tasks, each one a complete, self-contained Claude Code prompt ready to paste into a terminal. The developer can post the RCA back to Jira as a comment, create sub-tasks for each fix, assign them to team members, and track them through resolution — all without leaving CodeOps.

This workflow turns bug triage from a multi-hour manual process into a ten-minute automated investigation. The AI reads the ticket, reads the code, understands the architecture via the persona and directive system, and produces a targeted analysis that a senior engineer would recognize as thorough.

### Remediation & Task Generation

Every audit, compliance check, and bug investigation produces findings. CodeOps converts those findings into remediation tasks — ordered, grouped, and formatted as complete Claude Code prompts that follow the team's air-gap methodology. Each task file contains the full context an AI agent needs to implement the fix: the finding description, the file paths involved, the relevant code patterns, the expected behavior, the team's coding conventions, and explicit instructions to compile, test, commit, and push when finished. Tasks can be exported as individual Markdown files, as a ZIP archive, or pushed directly to Jira as issues with all fields pre-populated.

This is the mechanism that closes the loop. CodeOps identifies problems, explains them, and generates the exact instructions needed to fix them, in a format that AI agents consume directly. The human reviews the task list, approves or adjusts priorities, and fires the prompts. The AI executes them. The next audit confirms the fixes landed.

### Specification Compliance

For teams working against formal specifications — OpenAPI contracts, design documents, Figma mockups, architecture decision records — CodeOps provides a compliance mode that compares the actual implementation against the spec. Developers upload their specifications, and the AI agents examine the codebase for gaps: missing endpoints, incorrect response shapes, unimplemented business rules, UI elements that don't match the design. The output is a compliance matrix showing which requirements are met, partially met, or missing entirely, along with a compliance score and gap analysis report.

### Technical Debt Tracking

CodeOps identifies, categorizes, and trends technical debt across five dimensions: architecture, code, test, dependency, and documentation. Each debt item includes a severity assessment, effort estimate, and business impact rating. The system tracks debt over time, so teams can see whether their debt is growing or shrinking, which categories are most problematic, and which specific items have been open the longest. Debt items can be converted to remediation tasks and sent to Jira like any other finding.

### Dependency Health

A dedicated dependency scanning workflow examines package manifests, identifies outdated packages and known CVEs, and produces update task prompts. The system integrates with vulnerability databases to flag security issues and tracks the status of each vulnerability through resolution. Like all other CodeOps workflows, the output feeds directly into the task generation pipeline.

### Codebase Health Monitoring

CodeOps supports scheduled monitoring — daily, weekly, or triggered by commits — that runs automated audits and compares results against previous snapshots. When a health score drops below a team-configured threshold, the system fires alerts through email, Microsoft Teams webhooks, and in-app notifications. This gives teams continuous visibility into quality trends without manual intervention.

### Source Control Management

CodeOps provides a complete GitHub Desktop equivalent built into the native desktop application. Developers can browse organizations and repositories, clone repos with progress tracking, switch branches, create branches, commit changes, push, pull, view diffs with syntax highlighting, manage stashes, create and merge pull requests, view CI status badges, and browse commit history — all from within the CodeOps interface. The underlying implementation uses the GitHub REST API for remote operations and the local Git CLI via subprocess for local operations, wrapped in a provider abstraction that can extend to Azure DevOps or other VCS platforms in the future.

### Team Collaboration

CodeOps is a multi-tenant, team-oriented platform. Users belong to teams, teams own projects, and all data — findings, audits, health scores, personas, directives, tasks — is scoped to the team. Team members share the same view of project health, the same custom personas, the same coding directives, and the same integration configurations. Invitations, role management (owner, admin, member, viewer), and activity tracking are built into the core platform. Notifications flow through in-app alerts, email via AWS SES, and Microsoft Teams via incoming webhooks.

### Personas & Directives

The persona and directive system is one of CodeOps's most distinctive features. Personas define how each AI agent behaves — what it focuses on, how it calibrates severity, what output format it uses. Built-in personas ship with the application for each of the twelve agent types, but teams can create custom personas that override the defaults, share them across the team, set them as the default for a specific agent type, version them, and test them against sample code before deploying.

Directives are reusable context documents — Markdown files that get injected into agent prompts. A team might have a "Java Coding Standards" directive that specifies constructor injection, PreAuthorize patterns, and naming conventions, plus a project-specific directive for the payment service that describes its critical modules, PCI compliance requirements, and BigDecimal rules. Directives can be scoped to the team (apply to all projects) or to a specific project, and assignment is managed through a toggle interface.

The assembly order is deterministic: built-in persona, overridden by team persona if one exists for that agent type, plus team directives, plus project directives, plus job-specific context (Jira ticket data, user notes, spec references). The result is a fully assembled prompt that gives each AI agent deep, specific context about the team's standards and the project's architecture, every time it runs.

## The Control Plane — Complete

Everything described above exists today and is running as CodeOps v1.0. The Control Plane extended this foundation with additional backend modules (built into CodeOps-Server) and their corresponding frontend modules in the Flutter desktop client, plus an MCP module that ties everything together for AI agents. Together, these additions transformed CodeOps from a maintenance command center into a full-spectrum development operations platform — and that transformation is now complete.

**Architecture:** Two backend services — CodeOps-Server (monolith with modules for core, registry, logger, courier, relay, fleet, and mcp) and CodeOps-Vault (standalone, own encryption keyspace). One Flutter desktop client with all frontend modules including DataLens (client-side DBeaver clone with direct database connections). All 115 tasks across 13 phases delivered.

### The Registry — Knowing What You Have

As an AI-first team builds at five hundred times traditional speed, the number of services, databases, ports, routes, and cloud resources grows rapidly. Within weeks, a small team can produce an ecosystem that looks like what a hundred-person engineering organization built over years. Without a central catalog, this ecosystem becomes unmanageable — developers forget which ports are allocated, services step on each other's port ranges, dependency relationships are documented nowhere, and spinning up a local development environment requires tribal knowledge that lives in one person's head.

The Registry solves this by providing a single source of truth for every service in the ecosystem. When a new service is registered, the Registry allocates its ports from configurable ranges (HTTP APIs in one range, databases in another, caches in another), generates a complete identity kit (Docker container names, network names, volume names, database names, API route prefixes, CloudWatch log groups, Secrets Manager paths), and makes all of that information available to every other tool in the platform. The dependency graph engine tracks which services depend on which other services, can compute startup ordering via topological sort, and can perform impact analysis to answer the question "if I take down Service X, what breaks?" Solutions group related services into logical units, and workstation profiles let developers define named subsets of services to run locally for different tasks.

The Registry is not a static catalog. It drives configuration generation: docker-compose files, Spring Boot application.yml files, Claude Code prompt headers, and Terraform module stubs are all generated from Registry data. Change a port allocation in the Registry, and every generated configuration updates to match. This eliminates the class of bugs caused by stale configuration files that reference old port numbers or missing services.

### The Vault — Securing Everything from Day One

Every service needs credentials — database passwords, API keys, encryption keys, cloud provider tokens. In a traditional setup, these secrets live in .env files, docker-compose.yml environment blocks, and CI/CD variable stores, scattered across repositories with no versioning, no rotation, no audit trail, and no access control beyond file system permissions. At AI-first speed, where new services spin up in hours, this ad-hoc approach becomes dangerous quickly.

CodeOps-Vault provides encrypted secret storage with hierarchical path organization that mirrors the service structure from the Registry. Every write creates a new version, so secrets are never overwritten and any historical value can be retrieved. Access policies support wildcard path matching, multiple binding types (user, team, service), and deny-overrides-allow semantics. Rotation policies can be scheduled per secret or per path pattern, with Registry integration that knows which services consume which secrets.

For local development, Vault eliminates plaintext secrets entirely. When the Registry registers a new service that needs a database, Vault generates the credentials automatically. Service-to-service credentials are managed based on dependency declarations. For staging and production environments, Vault stores references to AWS Secrets Manager ARNs rather than the secrets themselves, acting as a unified interface regardless of where secrets actually live.

The transit encryption feature allows services to encrypt and decrypt data without storing it in the Vault, turning Vault into an encryption-as-a-service layer. Named encryption keys with versioning support key rotation without re-encrypting existing data through envelope encryption patterns.

### The Logger — Seeing Everything That Happens

When twelve AI agents run simultaneously against a codebase, or when a microservice ecosystem processes requests across a dozen services, the volume of log data produced is enormous, and the ability to search, correlate, and alert on it is critical. Traditional logging setups — Datadog at two hundred thousand to a million dollars a year, or self-hosted ELK stacks that require dedicated DevOps teams — are either prohibitively expensive or operationally burdensome.

CodeOps-Logger provides centralized log ingestion (via HTTP push and Kafka consumer), a structured query engine with full-text search and field-level filters, and a trap system that fires alerts when log patterns match configurable triggers. Traps can detect regex matches, keyword occurrences, frequency thresholds ("more than ten errors per minute from the payment service"), and absence patterns ("no logs from Service X for five minutes"). Alerts route to email, Microsoft Teams, Slack, or webhooks, with severity levels, acknowledgment tracking, and throttling to prevent alert storms.

The metrics collection system captures counters, gauges, histograms, and timers, with built-in Spring Actuator integration that automatically pulls JVM metrics, HTTP request metrics, and database pool metrics from any registered service. Time-series storage supports aggregation at configurable resolutions, and dashboards combine log streams, metric charts, and trace visualizations into shareable, auto-refreshing views.

Trace correlation is perhaps the most valuable feature for microservice teams. Every CodeOps service already propagates X-Correlation-ID headers through a shared request filter. Logger assembles these correlation IDs into cross-service request traces, visualized as waterfall timelines showing exactly how a request flowed through the ecosystem and where time was spent. When a request fails, the trace shows which service produced the error, and a single click navigates to the relevant log entries.

### Courier — Testing Every API From One Place

API testing in a traditional workflow means maintaining Postman collections that drift out of sync with the actual API, managing environment variables across local, staging, and production configurations, and sharing collections through export files or paid Postman team plans. For AI-first teams producing new endpoints at extreme velocity, this manual maintenance is unsustainable.

CodeOps-Courier is a full Postman replacement built into the platform. It supports all HTTP methods, GraphQL queries with schema introspection, and a complete request builder with parameter management, header configuration, body editing (JSON, XML, form data, file uploads, binary), and authorization handling (API key, Bearer, Basic, OAuth 2.0, JWT, inherit-from-parent). Pre-request and post-response scripts use the pm object API for assertions, variable manipulation, and chained requests. Collections support unlimited folder nesting, and the script execution order matches Postman exactly: collection pre-request through to request post-response and back up through folder and collection post-response scripts.

The critical differentiator is Registry integration. Courier can auto-discover every service registered in the Registry, fetch its OpenAPI specification, and generate a complete test collection with all endpoints, request bodies, and example data with a single click. Environment variables for base URLs and ports are generated from Registry data. When a service's API changes, regenerating the collection reflects the changes immediately, because the Registry and the OpenAPI spec are the source of truth.

The collection runner executes all requests in a collection sequentially, supports iterations with CSV or JSON data files, and produces detailed results reports exportable as JSON, CSV, or HTML. Code generation produces ready-to-use snippets from any request in ten or more languages. Request history logs every request sent with full request/response data, enabling replay, debugging, and auditing.

### DataLens — Managing Every Database From One Place

Database management in enterprise environments typically involves a mix of pgAdmin, DBeaver, DataGrip, and command-line psql, with each developer maintaining their own connection profiles and saved queries. Connection credentials are stored locally, often in plaintext configuration files, and there's no team-wide visibility into who is querying what.

CodeOps-DataLens is a full DBeaver replacement built entirely client-side within the Flutter desktop application. Like DBeaver itself, it connects directly to databases via native Dart TCP drivers — no server proxy, no backend service. It supports PostgreSQL, MySQL, MariaDB, SQLite, and SQL Server through pure Dart driver packages. Connection profiles are stored locally in Drift (SQLite) with passwords encrypted via flutter_secure_storage. Credentials can also be pulled directly from CodeOps-Vault rather than stored locally.

The database navigator provides a lazy-loading tree view from connections down through schemas, tables, views, functions, and sequences, with expansion into columns, indexes, constraints, and triggers — matching DBeaver's interface exactly.

The SQL editor supports multi-tab editing with syntax highlighting, autocomplete populated from database metadata, multiple execution modes (full script, selection, statement at cursor), EXPLAIN / EXPLAIN ANALYZE visualization, transaction control with auto-commit toggle, query history, saved scripts in organized folders, and parameterized queries. The data editor provides paginated grid display with inline editing, a pending-changes model that stages modifications locally before applying, foreign key navigation that lets developers click a reference to jump to the related row, and specialized viewers for JSON columns and binary data.

ER diagram generation produces interactive, auto-laid-out diagrams from database schemas using IDEF1X or Crow's Foot notation, with export to PNG and SVG. Data export supports CSV, JSON, SQL INSERT, XLSX, XML, and HTML, while the import wizard handles CSV column mapping and SQL script execution.

Because DataLens runs entirely in the desktop client, there is no server component, no backend database, and no network proxy between the user and their databases. All SQL execution happens via direct TCP connections from the Flutter app to the target database, exactly as DBeaver connects via JDBC. Connection profiles, saved queries, query history, snippets, and bookmarks are all stored locally in Drift (SQLite). This means DataLens works even when CodeOps-Server is offline — it has zero server dependencies.

### Scribe — Editing Code and Text Everywhere

Throughout the CodeOps platform, there are numerous places where developers need to edit structured text: SQL queries in DataLens, JavaScript test scripts in Courier, YAML configuration templates in the Registry, JSON secrets in Vault, log query patterns in Logger, Markdown personas and directives in the main CodeOps interface. Rather than implementing a separate text editor for each of these contexts, Scribe provides a single, shared editor widget built as a reusable Flutter component.

Scribe supports syntax highlighting for thirty or more languages, code folding, bracket matching, multi-cursor editing, find and replace with regex support, configurable font sizes and indentation, and line number display. For Markdown content, it provides a live side-by-side preview using GitHub Flavored Markdown rendering, scroll synchronization between the editor and preview panes, and auto-generated tables of contents from headings. A diff editor mode allows comparing two files side by side with additions and deletions highlighted.

As a standalone feature, Scribe functions as a multi-tab file editor with native file system integration (open, save, Save As via Flutter's file_picker), auto-save to local storage for crash recovery, session persistence that restores all open tabs on relaunch, and recent file tracking. But its primary value is as the shared foundation component consumed by every other module in the platform. Building Scribe first is a critical dependency: no other frontend module can be completed without the ScribeEditor widget.

### The MCP Gateway — Where Everything Comes Together for AI

The MCP Gateway is the feature that distinguishes CodeOps from a collection of developer tools and makes it a true AI-first development control plane. It is the answer to a question that no other product has even asked: what does an AI agent need to operate effectively across an entire development ecosystem?

Today, when a developer starts a Claude Code session to work on a service, they manually assemble context. They copy the CONVENTIONS.md file, paste the architecture document, reference the audit results, look up the relevant port numbers, find the database credentials, and hope that all of this information is current. If another developer worked on the same service yesterday, the audit file in the repo is already stale. If the team updated a coding convention last week, the CONVENTIONS.md in this repo might not reflect it. Every session starts with a context assembly problem, and the quality of the session depends heavily on how thoroughly (and recently) that context was assembled.

The MCP Gateway eliminates this problem entirely. When Claude Code connects to CodeOps via MCP, it calls a single initialization function and receives a complete, current context payload: the team's AI persona (behavioral identity, coding standards, testing requirements), the canonical CONVENTIONS.md, all project documents (CLAUDE.md, Architecture.md, Audit.md, OpenAPI.yaml), the full ecosystem context from the Registry (ports, dependencies, routes, related services), secret references from Vault, active team directives, and a summary of recent sessions on this project including what changed and which commits were involved. The AI starts every session with perfect, current context, assembled automatically from the authoritative source.

During the session, the AI can make additional MCP calls to any service in the platform. It can query logs to debug a failing test, execute SQL to verify data state after a migration, send HTTP requests through Courier to validate an endpoint it just built, check the dependency graph to understand what other services might be affected by its changes, and retrieve secrets for test configurations. Every one of these actions is logged, timestamped, and associated with the developer and project.

When the session ends, the AI writes back what happened: commit hashes, files changed, endpoints modified, tests added, coverage numbers, and a human-readable summary. CodeOps stores this as a session record and updates the project's documents so the next session starts from the new state. A team-wide activity feed shows what every AI session across every project produced, enabling coordination without meetings: "Adam's session just modified the Gateway's auth module — Services A and B have dependent endpoints that may need review."

This writeback-and-refresh cycle is what eliminates context staleness. The system of record is not a file in a repository that goes stale after every session. It is the CodeOps database, updated by every session, served fresh to every subsequent session. Convention changes propagate instantly to every developer and every AI session across every project, because conventions are served from a single authoritative source, not copied into thirty repositories.

The MCP Gateway also solves the team coordination problem that AI-first development creates. When one person with AI agents can produce what used to take a fifty-person team, the traditional coordination mechanisms — standups, sprint planning, code reviews — cannot keep pace. The activity feed, session history, and cross-project impact detection built into the MCP system provide a new kind of coordination that operates at the speed the work happens.

### Relay — Communicate Without Leaving CodeOps

When a team operates at AI-first velocity, the volume of events that need human awareness — audit completions, alert triggers, session completions, secret rotations, container failures — is enormous. Routing these through Slack or Teams means they compete with lunch discussions and meeting invites, with no structured integration back into the tools that produced them.

CodeOps-Relay is a full team messaging platform built as a CodeOps-Server module — channels, threads, direct messages, file sharing, reactions, presence, and search. But unlike standalone Slack or Teams, Relay is wired into every other service. Audit results auto-post to project channels. Logger traps route alerts into channels for team discussion. MCP session summaries appear in real time so the team knows what changed without anyone manually reporting it. Registry events, Vault rotation alerts, Courier test failures, Fleet container crashes — all flow into the relevant channels automatically with rich, clickable formatting that navigates directly to the source event.

Channels are automatically created for every project and every registered service, so there is always a place for platform events to land. And because Relay conversations are stored in the central database, AI agents can search team discussion history via MCP. "What did the team decide about the retry strategy?" becomes a question Claude Code can actually answer.

Relay uses WebSocket (STOMP over SockJS) for real-time message delivery, typing indicators, and presence broadcasts, with long-polling fallback for environments without WebSocket support.

### Fleet — Manage Containers Without Leaving CodeOps

As the number of services grows, managing local development environments becomes increasingly painful. Which containers need to be running? What order do they start in? Which ports are already allocated? What happens when a container crashes silently?

CodeOps-Fleet is container lifecycle management driven by the Registry, built as a CodeOps-Server module that communicates with the Docker Engine API. The Registry already knows every service, its ports, its dependencies, and its startup order. Fleet turns that into one-click actions: start a service, start a solution (a group of related services), start a workstation profile (a named set of solutions for a developer's typical workflow).

Fleet provides three levels of abstraction. Service profiles define a single container's configuration — image, ports, environment variables, volumes, health check, restart policy — auto-generated from Registry data. Solution profiles group related services (for example, "API Gateway + Auth + Database") and start them in dependency order, waiting for each to report healthy before starting the next. Workstation profiles combine solutions into a developer's complete environment ("Backend Dev" = Core Solution + Logger + Courier) that starts with a single click.

Health monitoring polls container health checks, detects unhealthy services, auto-restarts when policy allows, detects crash loops, and fires platform events to Relay so the team knows immediately. Container logs are streamable in the Fleet UI and can be piped to Logger for persistent storage and searching. AI agents via MCP can start and stop services during sessions to run integration tests against real containers — no human intervention required for infrastructure operations during development.

## Why CodeOps Is Necessary

The necessity of CodeOps flows from a simple observation: AI-first development changes the economics and logistics of software production so dramatically that the existing tool ecosystem becomes not just inefficient but fundamentally inadequate.

When AI writes all production code at hundreds of times traditional velocity, the human developer's role shifts from writing code to providing architectural oversight, making design decisions, and managing the operational environment in which the AI works. The developer needs to see everything — every service, every dependency, every log, every database, every API contract, every secret — from a single vantage point, because the AI is producing changes across the ecosystem faster than any human can track by switching between separate tools.

The integration between tools matters as much as the tools themselves. Knowing that a service exists (Registry) is useful. Knowing that it exists and its secrets are current (Vault) and its logs are clean (Logger) and its API tests pass (Courier) and its database schema is correct (DataLens) and the team has been discussing its retry strategy (Relay) and its containers are healthy (Fleet) and all of this is available to the AI working on it (MCP) — that is the operational picture that enables confident, high-velocity development. No combination of separate SaaS products provides this integrated view, because they were never designed to share context with each other or with AI agents.

The cost argument is also compelling. A mid-size enterprise team paying for Consul, Vault, Datadog, Postman Enterprise, DBeaver Pro, Slack Business+, and Docker Business is spending somewhere between six hundred thousand and two and a half million dollars per year. CodeOps replaces all of them with a self-hosted platform that runs on the team's own infrastructure, produces no usage-based bills, and adds capabilities — particularly the MCP Gateway — that none of the replaced products offer at any price.

But the deepest reason CodeOps is necessary is that it enables a fundamentally new workflow. In the traditional model, tools serve humans who write code. In the CodeOps model, tools serve both humans and AI agents through the same unified interface, with the tools themselves maintaining the shared context that makes each AI session productive. This is not an optimization of the old workflow. It is a new workflow that did not exist before and cannot be supported by tools designed for the old one.

---

# Part II — Technical Specification

---

## Executive Summary

CodeOps is an AI-powered software development operations platform. The system — a Flutter native desktop application (CodeOps-Client) backed by a Java 21/Spring Boot cloud service (CodeOps-Server) and a standalone secrets service (CodeOps-Vault) — provides codebase health management, QA automation, Jira-driven bug investigation, tech debt tracking, remediation task generation, service registry, secrets management, centralized logging, API testing, database management, team messaging, container orchestration, and an MCP Gateway for AI agent integration.

The **Control Plane** — a suite of self-hosted enterprise tools replacing expensive SaaS products — is fully built and integrated. Every module connects to CodeOps-Server authentication, team permissions, and the service registry. The **MCP (Model Context Protocol) Gateway** gives AI agents programmatic access to the entire operational surface, making CodeOps the backbone for AI-first development at team scale. All 115 tasks across 13 phases have been delivered.

### Products Replaced

| CodeOps Service | Replaces | Annual Cost Replaced |
|----------------|----------|---------------------|
| **Registry** | Consul + custom service catalogs | $50K–200K |
| **Vault** | HashiCorp Vault | $100K–500K |
| **Logger** | Datadog / Splunk / ELK | $200K–1M+ |
| **Courier** | Postman (Team/Enterprise) | $50K–200K |
| **DataLens** | DBeaver Pro + pgAdmin + DataGrip | $20K–100K |
| **Relay** | Slack Business+ / Microsoft Teams | $150K–500K+ |
| **Fleet** | Docker Business / Portainer Enterprise | $50K–150K |
| **Scribe** | VS Code + Notion code blocks | Productivity tool |
| **MCP Gateway** | No equivalent exists | Novel capability |
| **Total** | | **$620K–2.65M+/year** |

---

## Existing System — CodeOps v1.0 (Complete)

The entire platform — all backend modules, all frontend modules, all integration and polish tasks — is complete and running.

### CodeOps-Server (COMPLETE — All Modules Merged)

- **Repository:** `~/Documents/Github/CodeOps-Server`
- **Commit:** `2cf0617`
- **Tech Stack:** Java 21, Spring Boot 3.3.0, PostgreSQL 16, Redis, Kafka, AWS S3, AWS SES, Docker
- **Port:** 8095
- **Database:** `codeops` (~84 tables)
- **API Surface:** ~526 endpoints across 7 modules (core, registry, logger, courier, relay, fleet, mcp)
- **Entities:** 114 entity classes
- **Source Files:** 905 | **Test Files:** 243 | **Tests:** ~3,500+
- **Auth:** Self-managed JWT. MFA via TOTP and email.
- **Roles:** OWNER, ADMIN, MEMBER, VIEWER
- **RBAC:** `@PreAuthorize("hasRole('ADMIN')")` on all controllers
- **Modules:** Core (25 entities, ~140 endpoints), Registry (11 entities, ~78 endpoints), Logger (16 entities, ~104 endpoints), Courier (18 entities, ~62 endpoints), Relay (12 entities, ~52 endpoints), Fleet (14 entities, ~32 endpoints), MCP (8 entities, ~25 endpoints)

### CodeOps-Client (COMPLETE — All Frontend Modules)

- **Repository:** `~/Documents/Github/CodeOps-Client`
- **Platform:** Flutter 3.41.1 / Dart 3.11.0 — **macOS native desktop application**
- **Architecture:** Riverpod 2.x + GoRouter + Dio + Drift
- **Source Files:** 1,200+ | **Test Files:** 512+ | **Tests:** ~6,000+
- **Routes:** 85+ | **Screens:** 90+
- **Completed modules:** Scribe ✅, Registry UI ✅, Vault UI ✅, DataLens UI ✅, Logger UI ✅, Courier UI ✅, Relay UI ✅, Fleet UI ✅, MCP UI ✅, Unified Dashboard ✅, Global Search ✅, User Preferences ✅
- **API Surface Consumed:** ~420 HTTP endpoint methods (Server ~140, Logger ~104, Registry ~77, Vault ~67, Courier ~79, MCP ~30, external ~23)

### CodeOps-Registry (COMPLETE — Merged into Server)

- **Original Repository:** `~/Documents/Github/CodeOps-Registry` (archived)
- **Status:** ✅ Complete and merged into CodeOps-Server as `com.codeops.registry/` package
- **Entities:** 11 | **Enums:** 11 | **Endpoints:** ~78

### CodeOps-Vault (COMPLETE — Standalone)

- **Repository:** `~/Documents/Github/CodeOps-Vault`
- **Port:** 8097
- **Status:** ✅ Complete — 10 entities, 7 enums, 8 controllers, 67 endpoints, 628 tests
- **Architecture:** Standalone service. Own encryption keyspace, Shamir seal lifecycle. Only service that stays separate.

### CodeOps-Logger (COMPLETE — Merged into Server)

- **Original Repository:** `~/Documents/Github/CodeOps-Logger` (archived)
- **Status:** ✅ Complete and merged into CodeOps-Server as `com.codeops.logger/` package
- **Entities:** 16 | **Enums:** 10 | **Endpoints:** ~104

### CodeOps-Courier (COMPLETE — Merged into Server)

- **Original Repository:** `~/Documents/Github/CodeOps-Courier` (archived)
- **Status:** ✅ Complete and merged into CodeOps-Server as `com.codeops.courier/` package
- **Entities:** 18 | **Enums:** 7 | **Endpoints:** ~62

---

## System Architecture

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                     CodeOps-Client (Flutter Native Desktop)                   │
│                     macOS (primary) | Linux | Windows (future)                │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐    │
│  │ v1.0 Core: Home, Projects, GitHub, Audit, Compliance, Bugs, Tasks,  │    │
│  │ Tech Debt, Dependencies, Health, Personas, Directives, Settings     │    │
│  └──────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐        │
│  │Registry│ │ Vault  │ │ Logger │ │Courier │ │ Relay  │ │ Fleet  │        │
│  │  UI    │ │  UI    │ │  UI    │ │  UI    │ │  UI    │ │  UI    │        │
│  └────────┘ └────────┘ └────────┘ └────────┘ └────────┘ └────────┘        │
│                                                                              │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌──────────────────┐                     │
│  │DataLens│ │ Scribe │ │  MCP   │ │  Unified Search   │                     │
│  │  UI    │ │  UI    │ │  UI    │ │  & Dashboard      │                     │
│  └────────┘ └────────┘ └────────┘ └──────────────────┘                     │
│  (direct DB)  (local)                                                        │
└──────┬──────────────────────────────────────────────────────┬───────────────┘
       │ All modules except Vault + DataLens                  │ Vault only
       │                                                      │
┌──────▼──────────────────────────────────────────┐    ┌──────▼──────┐
│             CodeOps-Server (:8095)                │    │ CodeOps-Vault│
│             PG:5432 | Redis:6379 | Kafka:9092    │    │   (:8097)    │
│                                                  │    │   PG:5433    │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │    │              │
│  │  core/   │ │ registry/│ │ logger/  │        │    │ Secrets      │
│  │ auth,    │ │ services,│ │ logs,    │        │    │ Transit      │
│  │ teams,   │ │ ports,   │ │ traps,   │        │    │ Policies     │
│  │ users,   │ │ deps,    │ │ alerts,  │        │    │ Rotation     │
│  │ projects │ │ topology │ │ metrics  │        │    │ Seal/Unseal  │
│  └──────────┘ └──────────┘ └──────────┘        │    │ Audit        │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐        │    └──────────────┘
│  │ courier/ │ │  relay/  │ │  fleet/  │        │
│  │ requests,│ │ channels,│ │ docker,  │        │
│  │ envs,    │ │ threads, │ │ profiles,│        │
│  │ runner,  │ │ DMs,     │ │ health,  │        │
│  │ scripts  │ │ presence │ │ solutions│        │
│  └──────────┘ └──────────┘ └──────────┘        │
│  ┌──────────────────────────────────────┐      │
│  │              mcp/                     │      │
│  │  sessions, docs, context assembly,    │      │
│  │  tool proxy, activity feed            │      │
│  │  (direct injection to all modules)    │      │
│  └──────────────────────────────────────┘      │
└─────────────────────┬────────────────────────────┘
                      │ MCP Protocol
                ┌─────┴─────┐
                │ Claude Code│
                │ AI Agents  │
                └────────────┘
```

All modules in CodeOps-Server share one Postgres database, one Redis instance, one Kafka cluster, one JWT validation chain, one security config, one exception hierarchy, and one set of base infrastructure. Only Vault remains standalone with its own database and encryption keyspace.

DataLens is entirely client-side — direct TCP database connections via native Dart drivers, no server component.

---

## Service Inventory

### Backend Services (Post-Consolidation)

| Service | Port | Database | Repository |
|---------|------|----------|------------|
| CodeOps-Server | 8095 | codeops (Postgres:5432) | `AI-CodeOps/CodeOps-Server` |
| CodeOps-Vault | 8097 | codeops_vault (Postgres:5433) | `AI-CodeOps/CodeOps-Vault` |

### Server Modules (all in CodeOps-Server)

| Module | Package | API Prefix | Status |
|--------|---------|------------|--------|
| Core | `com.codeops.server/` | `/api/v1/` | ✅ Complete |
| Registry | `com.codeops.registry/` | `/api/v1/registry/` | ✅ Complete (merged) |
| Logger | `com.codeops.logger/` | `/api/v1/logger/` | ✅ Complete (merged) |
| Courier | `com.codeops.courier/` | `/api/v1/courier/` | ✅ Complete (merged) |
| Relay | `com.codeops.relay/` | `/api/v1/relay/` | ✅ Complete |
| Fleet | `com.codeops.fleet/` | `/api/v1/fleet/` | ✅ Complete |
| MCP | `com.codeops.mcp/` | `/api/v1/mcp/` | ✅ Complete |

### Infrastructure (docker-compose.yml in CodeOps-Server)

| Service | Port |
|---------|------|
| PostgreSQL (Server) | 5432 |
| PostgreSQL (Vault) | 5433 |
| Redis | 6379 |
| Zookeeper | 2181 |
| Kafka | 9092 |

### Frontend (All Modules Complete — CodeOps-Client)

All Control Plane UI modules are routes/pages within the Flutter desktop application. They follow the same architecture: Riverpod providers → Dio API services → backend endpoints (`:8095` for all modules except Vault at `:8097`). Scribe and DataLens are client-side only (no backend dependency). Cross-module navigation, unified dashboard, global search (Ctrl+K), and user preferences are fully integrated.

### Archived Repositories

| Repo | Status | Reason |
|------|--------|--------|
| CodeOps-Registry | 📦 Archived | Merged into CodeOps-Server |
| CodeOps-Logger | 📦 Archived | Merged into CodeOps-Server |
| CodeOps-Courier | 📦 Archived | Merged into CodeOps-Server |
| CodeOps-DataLens | 🗑️ Deleted | No backend — built entirely client-side |
| CodeOps-MCP | Never created | Built as Server module |
| CodeOps-Relay | Never created | Built as Server module |
| CodeOps-Fleet | Never created | Built as Server module |

**Active Repositories (3):**
- `AI-CodeOps/CodeOps-Server` — All backend modules
- `AI-CodeOps/CodeOps-Vault` — Standalone secrets service
- `AI-CodeOps/CodeOps-Client` — Flutter desktop application (all frontend modules)

---

## Shared Technology Stack (All Server Modules)

All modules within CodeOps-Server share the same infrastructure — no duplication:

- **Java 21**, **Spring Boot 3.3.0** (single POM)
- **PostgreSQL 16** (one database: `codeops`, shared via Hibernate DDL)
- **Hibernate** `ddl-auto: update` (dev), `validate` (prod with Flyway) — **No Flyway** in development
- **JWT validation** — CodeOps-Server issues and validates. Vault validates only via shared secret.
- **jjwt 0.12.6**, **MapStruct 1.5.5.Final**, **Lombok 1.18.42**
- **Testcontainers 1.19.8** for integration tests, **H2** for unit tests
- **Logback** with structured logging: human-readable (dev), JSON via LogstashEncoder (prod), WARN-only (test)
- **BaseEntity** pattern: UUID PK, `createdAt`/`updatedAt` via `@PrePersist`/`@PreUpdate`
- **Exception hierarchy**: `ServiceException` → `NotFoundException`, `ValidationException`, `AuthorizationException`
- **Request correlation**: `X-Correlation-ID` header propagated via `RequestCorrelationFilter`
- **100% test coverage**, **Javadoc on all classes and public methods** (excluding DTOs, entities, generated code)
- **CONVENTIONS.md** in repository root

### Module-Specific Dependencies

| Module | Extra Dependencies |
|--------|-------------------|
| Logger | spring-kafka (Kafka consumer), scheduling |
| Courier | graalvm-js:24.1.1, polyglot:24.1.1 (JS sandbox), jackson-dataformat-yaml |
| Relay | spring-websocket, spring-messaging (STOMP/SockJS) |
| Fleet | Docker Engine API client (HTTP over Unix socket) |
| MCP | No additional — uses direct `@Autowired` injection to all other modules |

### Frontend Stack (CodeOps-Client — Flutter)

All Control Plane UI modules integrate into the existing CodeOps-Client application:

- **Flutter 3.41.1** / **Dart 3.11.0**
- **Riverpod 2.x** state management (manual provider definitions, not @riverpod codegen)
- **GoRouter 14.8.1** with auth guards and NavigationShell
- **Dio 5.7.0** HTTP client with JWT auth interceptor, token refresh, error mapping, correlation IDs
- **Drift 2.23.1** local SQLite for offline caching
- **Material 3 dark theme** — background #1A1B2E, primary #6C63FF, secondary #00D9FF
- **Typography:** Inter (primary), JetBrains Mono (code)
- **fl_chart** for data visualization
- **flutter_markdown** for Markdown rendering
- **file_picker** for native file dialogs
- **window_manager** for desktop window management
- **ApiException sealed hierarchy**: BadRequest, Unauthorized, Forbidden, NotFound, Conflict, Validation, RateLimit, Server, Network, Timeout
- **ErrorPanel.fromException** with retry pattern on all async views
- **Existing patterns to follow:** Pages → Providers → Services → API Client → Server. `Provider` for singletons, `StateProvider` for UI state, `FutureProvider`/`.family` for async data, `StreamProvider` for reactive streams.

---

## Security Model

All services share the same security architecture as CodeOps-Server:

1. **Authentication** — JWT tokens issued by CodeOps-Server. All Control Plane services validate (never issue). Shared JWT secret across all services.
2. **Authorization** — RBAC via CodeOps-Server roles. Server roles: OWNER, ADMIN, MEMBER, VIEWER. All controllers use `@PreAuthorize("hasRole('ADMIN') or hasAuthority('specific:permission')")` — never just `hasAuthority` alone.
3. **Token flow** — Client stores JWT in OS keychain (macOS Keychain / Linux libsecret). Dio interceptor attaches `Authorization: Bearer {token}`. On 401, automatic refresh via `/api/v1/auth/refresh`. If refresh fails, logout.
4. **MFA** — Optional TOTP or email-based MFA via CodeOps-Server (COC-020, COC-021 complete).
5. **Encryption at rest** — Vault secrets encrypted with AES-256-GCM. DataLens connection passwords use same pattern.
6. **Rate limiting** — Per-service rate limits on auth-adjacent endpoints.
7. **CORS** — Configured per-service, allowing CodeOps-Client origins (localhost:3200 for Flutter web mode).
8. **Request correlation** — All services propagate `X-Correlation-ID` headers via `RequestCorrelationFilter`.
9. **Logging security** — Never log tokens, passwords, request/response bodies, Authorization headers.

---

# MODULE 1: Registry

**Package:** `com.codeops.registry/` (in CodeOps-Server)
**API Prefix:** `/api/v1/registry/`
**Status:** ✅ COMPLETE

**Purpose:** Service catalog, port allocation, dependency mapping, topology visualization, solution management, API route management, infrastructure resource tracking, configuration generation, and workstation profiles for all services in the ecosystem.

## 1.1 Service Registration & Discovery

- Register, discover, and manage microservices across the ecosystem
- Auto-generate slugs from service names (via `SlugUtils`)
- Track service health status via `ServiceStatus` enum: UP, DOWN, DEGRADED, MAINTENANCE, UNKNOWN
- Service types via `ServiceType` enum: API, FRONTEND, DATABASE, QUEUE, CACHE, GATEWAY, LIBRARY, OTHER
- Service lifecycle via `LifecycleState` enum: REGISTERED, ACTIVE, DEPRECATED, DECOMMISSIONED
- Metadata per service: name, slug, description, owner, team, repository URL, tech stack, version, environment

## 1.2 Port Allocation Engine

- Configurable port ranges per `PortType` enum: HTTP, HTTPS, GRPC, DATABASE, CACHE, QUEUE, MONITORING, DEBUG, FRONTEND, MANAGEMENT, CUSTOM
- Automatic port allocation with conflict detection across all registered services
- Per-environment port assignments via `Environment` enum: LOCAL, DEV, STAGING, PROD
- Port map visualization — visual grid showing allocated vs. available ports per range
- Permanent per-project allocations — a service always gets the same ports on every developer's machine
- Protocol tracking via `ProtocolType` enum: TCP, UDP, HTTP, HTTPS, GRPC, WEBSOCKET

## 1.3 Dependency Graph

- Directed graph of service-to-service dependencies
- Dependency types via `DependencyType` enum: RUNTIME, BUILD, OPTIONAL, DEV_ONLY
- BFS impact analysis — "if I take down Service X, what breaks?"
- Topological sort for startup ordering — determines correct service boot sequence
- Cycle detection — prevents circular dependency declarations

## 1.4 Solutions

- Logical groups of services (e.g., "CodeOps Platform", "Elaro Core")
- `SolutionStatus` enum: ACTIVE, ARCHIVED, DRAFT
- Member management — add/remove services from solutions
- Health aggregation — solution health derived from member service health
- Display ordering — configurable sort order for dashboard presentation

## 1.5 API Route Management

- Route prefix registration per service (e.g., `/api/v1/registry`)
- `RouteStatus` enum: ACTIVE, DEPRECATED, DISABLED
- Collision detection including prefix overlap detection
- Gateway integration — route table feeds API gateway configuration

## 1.6 Infrastructure Resources

- Track cloud/infrastructure resources per service
- `ResourceType` enum: S3_BUCKET, SQS_QUEUE, SNS_TOPIC, CLOUDWATCH_LOG_GROUP, SECRETS_MANAGER, RDS_INSTANCE, ELASTICACHE, IAM_ROLE, LAMBDA, DYNAMODB, CLOUDFRONT, ROUTE53, ECS_SERVICE, EKS_CLUSTER, OTHER
- Resource ownership — which service owns which resource
- Orphan detection — identify resources not claimed by any active service

## 1.7 Configuration Generation

- **docker-compose.yml** — generate from registry data with correct port mappings, container names, network names, volume names, dependency ordering
- **application.yml** — generate Spring Boot configuration with server ports, database URLs, service discovery URLs
- **Claude Code prompt headers** — generate context header section for AI prompts with ports, dependencies, routes, ecosystem state
- **Terraform module stubs** — generate resource naming and variable files from registry data
- Templates are registry-driven — add a new service and all generated configs update automatically

## 1.8 Topology Viewer

- Visual map of the entire ecosystem showing all services and their connections
- Solution grouping — services clustered by solution membership
- Interactive: click a service to see detail, dependencies, port allocations
- Filterable by solution, service type, health status, environment

## 1.9 Workstation Profiles

- Named startup configurations for running subsets of services locally
- Profile defines which services to start, in what order (from dependency graph), and which environment config to use
- One-click start/stop of entire profiles

## 1.10 Service Identity Kit

When a new service is registered, the Registry generates a complete identity: allocated ports (application, database, cache, monitoring, frontend), database name, Docker container/network/volume names, API route prefix, CloudWatch log group name, Secrets Manager path prefix. This identity kit feeds docker-compose generation, Terraform modules, Claude Code prompts, and CI/CD pipelines.

## Registry Data Model

**11 entities:** Service, ServicePort, PortRange, Solution, SolutionMember, Dependency, ApiRoute, InfraResource, WorkstationProfile, ProfileMember, TopologyLayout
**11 enums:** ServiceType, ServiceStatus, LifecycleState, PortType, ProtocolType, Environment, DependencyType, SolutionStatus, RouteStatus, ResourceType, InfraStatus
**Endpoints:** ~78

---

# SERVICE 2: CodeOps-Vault (Standalone)

**Repository:** `AI-CodeOps/CodeOps-Vault`
**Port:** 8097 | **Database:** codeops_vault (Postgres:5433)
**Status:** ✅ COMPLETE — 10 entities, 7 enums, 8 controllers, 67 endpoints, 628 tests

**Architecture:** Vault is the ONLY standalone service. It maintains its own database, encryption keyspace, and Shamir seal lifecycle. This isolation is a security requirement — compromise of CodeOps-Server must not compromise the encryption master key.

**Purpose:** Secrets management — encrypted key-value store with versioning, rotation, access policies, dynamic secrets, transit encryption, seal/unseal, and audit trails. Replaces HashiCorp Vault ($100K–500K/year).

## 2.1 Secret Storage

- Encrypted key-value pairs organized by hierarchical path (e.g., `/services/talent-app/database/password`)
- AES-256-GCM encryption at rest
- Path-based organization mirrors service structure from Registry
- Secret types: static (key-value), dynamic (generated on demand), reference (pointer to external store like AWS Secrets Manager)
- Metadata per secret: description, owner, creation date, last accessed, expiration

## 2.2 Versioning

- Every write creates a new version — secrets are never overwritten
- Read current version or any historical version
- Version metadata: author, timestamp, change description
- Configurable version retention (keep last N versions or keep for N days)
- Diff between versions

## 2.3 Secret Rotation

- Scheduled rotation policies per secret or per path pattern
- Rotation strategies: generate random, call external API, invoke custom script
- Registry integration — rotation knows which services use which secrets
- Rotation history and status tracking
- Alert on rotation failures

## 2.4 Dynamic Secrets

- Short-lived database credentials generated on demand
- Lease-based lifecycle — credentials auto-expire after TTL
- Supported backends: PostgreSQL, MySQL (extensible)
- Lease tracking and revocation

## 2.5 Access Policies

- Fine-grained ACLs with wildcard path matching (e.g., `/services/talent-app/*`)
- Policy types: read, write, delete, list, rotate
- Bindings: user-level, team-level, service-level
- Deny rules override allow rules
- Policy evaluation with audit logging

## 2.6 Audit Trail

- Every operation logged: read, write, delete, list, rotate, policy change, seal/unseal
- Log fields: timestamp, actor (user or service), operation, path, source IP, success/failure
- Queryable audit log with time-range filters
- Integration with Logger for centralized audit visibility

## 2.7 Transit Encryption

- Encrypt/decrypt data without storing it — Vault acts as encryption-as-a-service
- Named encryption keys with versioning
- Key rotation without re-encrypting existing data (envelope encryption)
- Operations: encrypt, decrypt, rewrap, generate data key

## 2.8 Seal/Unseal

- Master key management — Vault starts sealed, must be unsealed to operate
- Shamir's secret sharing — master key split into N shares, M required to unseal
- Auto-unseal option for development environments
- Seal status endpoint for monitoring

## 2.9 Local Development Secrets Management

- Replaces `.env` files and hardcoded credentials in docker-compose.yml and application.yml
- Secret generation at service registration time — when Registry registers a new service needing a database, Vault generates credentials automatically
- Service-to-service credentials managed based on Registry dependency declarations
- Environment-aware: for local/dev, Vault owns secrets directly; for staging/prod, stores references to AWS Secrets Manager ARNs
- Eliminates plaintext secrets from project directories entirely

## Vault Data Model

**~10 entities** | **~45 endpoints**
Entities include: Secret, SecretVersion, SecretMetadata, AccessPolicy, PolicyBinding, RotationPolicy, RotationHistory, DynamicLease, TransitKey, AuditEntry

---

# MODULE 3: Logger

**Package:** `com.codeops.logger/` (in CodeOps-Server)
**API Prefix:** `/api/v1/logger/`
**Status:** ✅ COMPLETE

**Purpose:** Centralized logging, metrics, alerting, trace correlation, dashboards, and anomaly detection. Replaces Datadog/Splunk/ELK ($200K–1M+/year).

## 3.1 Log Ingestion

- **HTTP ingest** — structured JSON logs via REST endpoint
- **Kafka consumer** — subscribe to log topics for high-throughput ingestion (Kafka running at localhost:9092 in CodeOps-Server's docker-compose)
- Structured parsing — extract fields from JSON, key-value pairs, common log formats
- Source tagging — logs tagged with service identity from Registry
- Batch ingestion for bulk historical import
- Rate limiting and back-pressure handling

## 3.2 Log Query Engine

- Full-text search across all log fields
- Structured filters: service, level (TRACE, DEBUG, INFO, WARN, ERROR, FATAL), time range, correlation ID, custom fields
- SQL-like query language for complex queries
- Pagination and streaming for large result sets
- Saved queries and query history

## 3.3 Log Traps

- Pattern-based alerting — triggers fire when log patterns match
- Trigger types: regex match, keyword match, frequency threshold, absence detection
- Trap actions: send alert, execute webhook, create incident
- Trap testing against historical logs before activating

## 3.4 Alert System

- Alert channels: email (via CodeOps-Server's SES integration), webhook, Microsoft Teams (via existing Teams webhook pattern from CodeOps-Server), Slack
- Alert routing rules, severity levels (INFO, WARNING, CRITICAL)
- Acknowledgment, resolution tracking, notification throttling

## 3.5 Metrics Collection

- Metric types: counters, gauges, histograms, timers
- Time-series storage with configurable resolution
- Spring Actuator integration — auto-collect JVM, HTTP, database pool metrics from registered services
- Custom metrics via HTTP push
- Aggregation: sum, avg, min, max, percentiles (p50, p95, p99)

## 3.6 Trace Correlation

- Cross-service request tracing via `X-Correlation-ID` propagation (already implemented in all CodeOps services via `RequestCorrelationFilter`)
- Span assembly — reconstruct full request flow across multiple services
- Waterfall visualization — timeline view showing each service's processing time
- Root cause identification — trace shows where failures originated

## 3.7 Dashboards

- Pre-built dashboards: system overview, per-service health, error rates, latency, log volume
- Custom dashboards with configurable widget layouts
- Widget types: log stream, time-series chart, counter, gauge, table, heatmap, pie chart, bar chart
- Dashboard sharing (team-visible by default), auto-refresh, templates

## 3.8 Anomaly Detection

- Baseline pattern learning per service for log volume, error rates, latency
- Deviation alerting when metrics deviate significantly from baseline
- Configurable sensitivity thresholds
- Anomaly history correlated with deployments

## 3.9 Retention Management

- Configurable retention policies per log source, severity, or age
- Automatic purge of expired logs
- Archival to cold storage (S3) before deletion
- Storage usage monitoring

## Logger Data Model

**16 entities** | **10 enums** | **~104 endpoints**
Entities include: LogEntry, LogSource, LogTrap, TrapCondition, AlertChannel, AlertRule, AlertHistory, Metric, MetricSeries, MetricDataPoint, Dashboard, DashboardWidget, TraceSpan, RetentionPolicy, AnomalyBaseline, AnomalyDetection

---

# MODULE 4: Courier

**Package:** `com.codeops.courier/` (in CodeOps-Server)
**API Prefix:** `/api/v1/courier/`
**Status:** ✅ COMPLETE

**Purpose:** Full-featured, self-hosted API testing and development platform. Replaces Postman Team/Enterprise ($50K–200K/year).

## 4.1 Request Builder

- **Protocol support:** HTTP/REST (all methods: GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS), GraphQL (query, mutation, subscription with schema introspection)
- **Params tab** — query parameters as key-value pairs with enable/disable toggles, auto-sync with URL, bulk edit
- **Headers tab** — key-value with toggles, auto-populated defaults, header presets
- **Body tab** — none, form-data (including file uploads), x-www-form-urlencoded, raw (JSON/XML/HTML/Text/YAML), binary, GraphQL (query + variables)
- **Authorization tab** — No Auth, API Key, Bearer Token, Basic Auth, OAuth 2.0 (authorization code, client credentials, implicit, password), JWT Bearer, Inherit from parent
- **Scripts tab** — pre-request and post-response JavaScript with `pm` object API. `pm` provides: `pm.request`, `pm.response`, `pm.environment`, `pm.globals`, `pm.variables`, `pm.expect`, `pm.sendRequest`
- **Settings tab** — follow redirects, timeout, SSL verification, proxy

## 4.2 Response Viewer

- Body display modes: Pretty (syntax-highlighted), Raw, Preview (rendered HTML), Visualize (custom rendering)
- Headers, Cookies (parsed), Test Results (pass/fail from assertions)
- Status bar: HTTP status, response time (ms), response size, content type

## 4.3 Collections

- Hierarchy: Collection → Folder (unlimited nesting) → Request
- Script execution order matches Postman: Collection pre → Folder pre → Request pre → HTTP call → Request post → Folder post → Collection post
- Import: Postman Collection v2.1 JSON, OpenAPI 3.x, cURL commands
- Export: Postman v2.1 JSON, OpenAPI 3.x

## 4.4 Environments & Variables

- Variable scopes (resolution order): Global → Collection → Environment → Local
- `{{variableName}}` syntax in URLs, headers, body, scripts
- Secret variables — masked in UI, never exported, stored encrypted
- Environment management: create, clone, edit, delete, switch active

## 4.5 Sharing & Collaboration

- Share collections with team members via CodeOps-Server teams
- Permission levels: Viewer, Editor, Admin
- Fork and merge collections with conflict resolution
- Change history

## 4.6 Collection Runner

- Execute all requests sequentially
- Iterations with CSV/JSON data files
- Configurable delay between requests
- Results report: pass/fail per request, timing, assertions
- Export results: JSON, CSV, HTML

## 4.7 Code Generation

- Generate code snippets from any request in 10+ languages: cURL, Python (requests), JavaScript (fetch, axios), Java (HttpClient, OkHttp), C# (HttpClient), Go, Ruby, PHP, Swift, Kotlin

## 4.8 Request History

- Automatic logging of every request with full request/response data
- Searchable by URL, method, status code, time range
- Replay and save-to-collection

## 4.9 Registry Integration

- Auto-discover services from CodeOps-Registry
- One-click collection generation from a service's OpenAPI spec
- Environment sync — auto-generate variables (base URLs, ports) from Registry data

## Courier Data Model

**18 entities, 7 enums** | **~62 endpoints**
Entities include: Collection, Folder, Request, RequestHeader, RequestParam, RequestBody, RequestAuth, RequestScript, Environment, EnvironmentVariable, GlobalVariable, CollectionShare, Fork, MergeRequest, RunResult, RunIteration, RequestHistory

---

# MODULE 5: DataLens (Client-Side Only)

**Integrated into:** CodeOps-Client (Flutter)
**Backend:** None — all client-side, direct TCP database connections
**Status:** ✅ COMPLETE

**Purpose:** Full DBeaver replacement — multi-database management, SQL editor, ER diagrams, data editor, import/export. 100% client-side, exactly like DBeaver uses JDBC drivers. Replaces DBeaver Pro + pgAdmin + DataGrip ($20K–100K/year).

**Architecture:** Native Dart database drivers connect directly to target databases via TCP. No server proxy. Connection profiles, saved queries, query history, snippets, and bookmarks stored locally in Drift (SQLite). Works even when CodeOps-Server is offline.

## 5.1 Connection Manager

- Multi-database via native Dart TCP drivers: PostgreSQL (`postgres` package), MySQL/MariaDB (`mysql_client` package), SQLite (`sqlite3` FFI), SQL Server (`tds_client` or ODBC FFI)
- Connection profiles stored in Drift (local SQLite): name, host, port, database, username, password (encrypted via flutter_secure_storage), SSL config
- Connection groups, test connection, Registry auto-discover
- Vault integration — "Fetch from Vault" button for credential lookup from CodeOps-Vault

## 5.2 Database Navigator

- Lazy-loading tree: Connection → Schema → Tables/Views/Functions/Sequences
- Table expansion: Columns, Indexes, Constraints (PK, FK, unique, check), Triggers
- Filter/search objects by name, drag table name into SQL editor

## 5.3 SQL Editor

- Multi-tab query editing
- Syntax highlighting with database-dialect awareness
- Autocomplete: table names, column names, SQL keywords, functions, schema names
- Execute modes: full script, selected text, statement at cursor
- EXPLAIN / EXPLAIN ANALYZE visualization
- Transaction control: auto-commit toggle, COMMIT/ROLLBACK
- Query history, script management, parameterized queries
- Multiple result sets display

## 5.4 Data Editor

- Paginated grid: sortable, resizable, filterable columns
- Inline editing with pending changes model (apply/revert)
- Row operations: insert, delete, duplicate
- NULL handling, FK navigation, JSON column viewer, binary/LOB display

## 5.5 Schema/Metadata Browser

- Table DDL, column details, index/constraint/trigger details
- Edit metadata (rename, add/drop columns) with DDL preview before execution

## 5.6 ER Diagrams

- Auto-generated from schema: full schema or single table with FK references
- IDEF1X / Crow's Foot notation
- Interactive drag/zoom, layout persistence
- Export: PNG, SVG, PDF

## 5.7 Data Export

- Formats: CSV, JSON, SQL INSERT, XLSX, XML, HTML
- Scope: entire table, query results, selected rows
- Configurable options per format

## 5.8 Data Import

- CSV import with column mapping wizard
- SQL script import
- Table-to-table transfer across connections

## 5.9 Database Administration

- Active sessions (view/kill), table statistics, database sizes, lock monitoring
- PostgreSQL-specific: pg_stat_activity, pg_locks, pg_stat_user_tables, index usage, VACUUM status

## 5.10 Search

- Metadata search, full-text data search, DDL search across schemas

## DataLens Data Model

No backend, no server database. All state is local Drift (SQLite) tables + Riverpod providers:

**Drift tables:** ConnectionProfile, ConnectionGroup, SavedQuery, QueryFolder, QueryHistory, QuerySnippet, TableBookmark, DiagramLayout
**Providers:** connection state, schema cache, query execution, results, editor tabs, navigator tree

---

# MODULE 6: CodeOps-Scribe

**Integrated into:** CodeOps-Client (Flutter)
**Backend:** None — all client-side
**Status:** ✅ COMPLETE

**Purpose:** Full-featured code and text editor built as a Flutter widget. Edit plain text, Markdown, JSON, YAML, SQL, Java, JavaScript, TypeScript, Python, Dart, and other languages within the CodeOps desktop app. Provides a shared editor component consumed by Courier (scripts), DataLens (SQL), Logger (queries), Registry (configs), and Vault (secret editing).

**Note:** Since CodeOps-Client is a Flutter native desktop application (not a web app), Scribe uses a Flutter-native code editor solution rather than Monaco Editor. The shared `ScribeEditor` widget is the Flutter equivalent of what Monaco provides in web contexts.

## 6.1 Multi-Tab File Editor

- Tab management: open, close, reorder, close-all/close-others, unsaved indicator
- File open: native file picker (file_picker package, already in CodeOps-Client), drag-and-drop, new blank file with language selector, open from URL
- File save: native save dialog, Save As, Ctrl+S
- Auto-save to local storage as crash recovery (configurable interval)

## 6.2 Shared `ScribeEditor` Widget

Core reusable editor component at `lib/widgets/scribe/scribe_editor.dart`, consumed by:

| Consumer Module | Usage |
|----------------|-------|
| **Courier UI** | Script editors (pre-request, post-response JavaScript) |
| **DataLens UI** | SQL editor (multi-tab, autocomplete) |
| **Logger UI** | Log query editor, trap pattern editor |
| **Registry UI** | Config template editor (YAML, JSON, Dockerfile) |
| **Vault UI** | Secret value editor (JSON, YAML) |
| **Relay UI** | Message composer (Markdown) |
| **MCP UI** | Document editor, convention manager, context viewer |

**Critical Build Order:** ScribeEditor must be built FIRST among all frontend modules. All other Control Plane UI modules depend on it.

## 6.3 Editor Features

- Syntax highlighting for 30+ languages
- Code folding, bracket matching, auto-close brackets/quotes
- Multi-cursor editing
- Find & Replace with regex support
- Go to line, command palette
- Word wrap (on/off/bounded), configurable font size (12–24px)
- Indentation: spaces or tabs, configurable width (2/4/8)
- Line numbers (on/off/relative)

## 6.4 Markdown Support

- Live preview: side-by-side split (editor left, rendered Markdown right)
- GitHub Flavored Markdown rendering (using flutter_markdown, already in CodeOps-Client)
- Scroll sync between editor and preview
- Table of contents from headings

## 6.5 Diff Editor

- Side-by-side diff: compare two files with additions/deletions highlighted
- Inline diff: unified view
- Select two open tabs to compare

## 6.6 Session Persistence

- Open tabs and content persisted locally (Drift or SharedPreferences)
- Restore full state on relaunch
- Recent files list with quick re-open

## 6.7 Theming

- Follows CodeOps-Client dark theme (#1A1B2E background, #6C63FF primary)
- Light theme option
- Syntax theme matching editor background

## 6.8 Status Bar

- Language mode picker, line/column position, encoding, line ending indicator, file size

## 6.9 Keyboard Shortcuts

Ctrl+N (new), Ctrl+O (open), Ctrl+S (save), Ctrl+W (close tab), Ctrl+Tab (next tab), Ctrl+F (find), Ctrl+H (replace), Ctrl+G (go to line), Ctrl+/ (toggle comment), Ctrl+D (select next occurrence)

## Scribe Data Model

No backend, no database tables. State management via Riverpod providers + local persistence:
- `ScribeState`: tabs, activeTabId, settings, recentFiles
- `ScribeTab`: id, fileName, language, content, originalContent, isDirty, cursorPosition, scrollPosition
- `ScribeSettings`: theme, fontSize, tabSize, insertSpaces, wordWrap, minimap, lineNumbers, autoSave

---

# MODULE 7: Relay

**Package:** `com.codeops.relay/` (in CodeOps-Server)
**API Prefix:** `/api/v1/relay/`
**Status:** ✅ COMPLETE

**Purpose:** Full team messaging platform with deep integration into every other CodeOps module. Channels, threads, direct messages, file sharing, reactions, presence, and search — wired so that platform events auto-post to relevant channels. Replaces Slack Business+ / Microsoft Teams ($150K–500K+/year).

## 7.1 Channels

- Channel types via `ChannelType` enum: PUBLIC (anyone joins), PRIVATE (invite only), PROJECT (auto-created per project, team members auto-joined), SERVICE (auto-created per registered service)
- Channel CRUD: create, rename, archive, delete
- Member management: join, leave, invite, kick
- Channel settings: name, description, topic, pinned messages
- Auto-channel creation: when a project is created in CodeOps-Server, a PROJECT channel is automatically created; when a service is registered in Registry, a SERVICE channel is created
- Starred channels pinned to top of sidebar

## 7.2 Messages & Threads

- Send, edit, delete messages in channels
- Threaded replies — message has optional `parentId` forming a thread
- Rich text: Markdown rendering (bold, italic, code blocks, links, lists)
- @mentions: `@user`, `@channel`, `@here`, `@all`
- Message search: full-text across all channels and DMs
- Cursor-based pagination for real-time message feeds
- Unread count tracking per user per channel
- Read receipts
- Pinned messages per channel

## 7.3 Direct Messages

- 1:1 direct conversations
- Group DMs (multi-user)
- Same features as channel messages: threads, reactions, files, Markdown
- Conversation list with last message preview and unread badges

## 7.4 Reactions & File Attachments

- Emoji reactions on messages: add/remove, aggregated counts, "you reacted" indicator
- File uploads: multipart upload, store locally (dev) or S3 (prod)
- Image thumbnails for image attachments
- File size limits and supported type validation
- Download endpoint
- File gallery per channel (browse all shared files)

## 7.5 Presence

- User status via `PresenceStatus` enum: ONLINE, AWAY, DND (Do Not Disturb), OFFLINE
- Heartbeat-based tracking (WebSocket ping or HTTP poll)
- Last seen timestamp
- Presence updates broadcast to relevant channels
- Auto-away after configurable idle timeout
- DND mode suppresses notifications
- Custom status text

## 7.6 Platform Event Integration

This is the critical integration layer that makes Relay fundamentally different from standalone Slack/Teams.

- `PlatformEventType` enum: AUDIT_COMPLETED, ALERT_FIRED, SESSION_COMPLETED, SECRET_ROTATED, CONTAINER_CRASHED, SERVICE_REGISTERED, DEPLOYMENT_COMPLETED
- **PlatformEventService** receives internal events from other modules and posts formatted messages to appropriate channels:
  - Audit completed → project channel: "🔍 Audit completed on ProjectX: Health score 87, 3 critical findings"
  - Logger alert fired → service channel: "🚨 Alert: Error rate exceeded threshold on api-gateway"
  - MCP session completed → project channel: "✅ Adam completed session on ProjectX: 3 files changed, 45 tests added, commit abc123"
  - Secret rotated → service channel: "🔑 Database credentials rotated for api-gateway"
  - Container health failure → service channel: "⛔ Container api-gateway unhealthy — restarting"
  - Service registered → #general: "📦 New service registered: payment-service :8104"
- Configurable per team: which event types route to which channels, mute options
- Event messages include clickable links that navigate directly to the source (click project → project page, click service → Registry detail, click session → MCP session detail)

## 7.7 WebSocket Real-Time

- Spring WebSocket + STOMP over SockJS
- Per-user WebSocket sessions authenticated via JWT
- Subscribe to channels and conversations
- Real-time message delivery
- Typing indicators
- Presence broadcasts
- Connection lifecycle (connect/disconnect, reconnect with message catch-up)
- Fallback: long-polling for environments without WebSocket support

## 7.8 Search

- Global message search: full-text across channels and DMs
- Filter by channel, user, date range, has:file, has:reaction
- Results with surrounding context (messages before/after)
- Click result → navigate to message in channel

## Relay Data Model

**12 entities, 8 enums** | **~52 endpoints**
Entities include: Channel, ChannelMember, Message, MessageThread, DirectConversation, DirectMessage, Reaction, FileAttachment, PinnedMessage, ReadReceipt, UserPresence, PlatformEvent

---

# MODULE 8: Fleet

**Package:** `com.codeops.fleet/` (in CodeOps-Server)
**API Prefix:** `/api/v1/fleet/`
**Status:** ✅ COMPLETE

**Purpose:** Container lifecycle management driven by Registry data. Docker Engine API integration for start/stop/restart, health monitoring, log streaming, and multi-level abstraction (service → solution → workstation profiles). Replaces Docker Business / Portainer Enterprise ($50K–150K/year).

## 8.1 Docker Engine Integration

- Docker Engine API client: HTTP over Unix socket (`/var/run/docker.sock`) or TCP
- Container operations: create, start, stop, restart, remove, inspect, list
- Image operations: list, pull, remove, prune
- Volume operations: list, create, remove, prune
- Network operations: list, create, remove, connect/disconnect containers
- Exec into container
- Stats streaming: CPU, memory, network I/O, disk I/O per container

## 8.2 Container Management

- Start/stop/restart containers by service name — resolved via Registry
- Auto-configure from Registry data: port mappings, environment variables, database credentials from Vault, network settings
- Health check polling at configurable intervals
- Container status tracking persisted in database
- Log capture: tail N lines, stream live, pipe to Logger module for persistent storage and searching
- Restart policies: NO, ALWAYS, ON_FAILURE, UNLESS_STOPPED
- `ContainerStatus` enum: RUNNING, STOPPED, RESTARTING, REMOVING, PAUSED, EXITED, DEAD, CREATED

## 8.3 Service Profiles

- One service = one container configuration: image, ports, environment variables, volumes, health check, restart policy
- Auto-generated from Registry service registration — when Registry registers a service, Fleet creates its profile
- Edit profile to override image tag, additional env vars, volume mounts, restart policy
- Start/stop individual services
- "Regenerate from Registry" to refresh config after Registry changes

## 8.4 Solution Profiles

- Named groups of services that start together in dependency order
- Dependency order computed from Registry dependency graph
- Example: "API Gateway + Auth + Database" starts Postgres first, waits for healthy signal, then Auth, then Gateway
- Start solution: progress indicator per service (starting → healthy → done)
- Stop solution: reverse dependency order
- Solution health: all green = healthy, any red = degraded
- CRUD: create, clone, edit, delete solutions

## 8.5 Workstation Profiles

- Named sets of solutions for a developer's typical workflow
- Example: "Backend Dev" = Core Solution + Logger + Courier
- **One-click start:** starts all solutions in order with full progress display
- **One-click stop:** stops everything
- "Set as default" → auto-offer on app launch
- Custom overrides per workstation: extra env vars, port remaps

## 8.6 Health Monitoring

- Poll container health checks continuously
- Detect unhealthy → auto-restart if policy allows
- Crash loop detection: 3+ restarts in 5 minutes → stop container and fire alert
- Platform events to Relay on health failures (via PlatformEventService)
- Aggregate fleet health: total containers, running, stopped, unhealthy
- Resource usage summaries: total CPU, memory across fleet

## Fleet Data Model

**14 entities, 4 enums** | **~32 endpoints**
Entities include: ContainerInstance, ServiceProfile, SolutionProfile, SolutionService, WorkstationProfile, WorkstationSolution, ContainerHealthCheck, ContainerLog, VolumeMount, NetworkConfig

---

# MODULE 9: MCP Gateway

**Package:** `com.codeops.mcp/` (in CodeOps-Server)
**API Prefix:** `/api/v1/mcp/`
**Status:** ✅ COMPLETE

**Purpose:** MCP (Model Context Protocol) server that gives AI agents programmatic access to the entire CodeOps ecosystem. This is the feature that transforms CodeOps from a developer tool suite into the **AI-First Development Control Plane** — the operational backbone for AI-first development at team scale. No equivalent exists in the market.

**Architecture Advantage:** Because MCP is a module inside CodeOps-Server, it accesses Registry, Logger, Courier, Relay, and Fleet services via direct `@Autowired` Java injection — zero network hops, zero HTTP overhead, zero serialization cost. Only Vault requires an HTTP call (separate service). This is fundamentally faster and more reliable than the original multi-service architecture where MCP would have needed HTTP calls to every backend.

## 9.1 Gateway Architecture

- **Single MCP endpoint** — agents configure one connection, get access to all CodeOps services
- **Protocol support:** MCP over stdio, SSE, HTTP
- **JWT authentication** — validates tokens from CodeOps-Server (same auth as all modules)
- **Dynamic tool registration** — tool definitions generated from services in Registry. Add a service to Registry, the AI immediately has tools to interact with it.
- **Internal routing** — MCP calls Registry, Logger, Courier, Relay, Fleet services via direct Java method invocation (same JVM). Only Vault requires HTTP.
- **Response aggregation** — combines data from multiple modules into cohesive context payloads
- **Session management** — tracks active AI sessions, associates with developers and projects
- **Audit logging** — every MCP tool call logged with developer, project, session, timestamp, result

## 9.2 AI Session Lifecycle

### Session Initialization

When Claude Code (or any MCP-compatible agent) starts a session:

1. Agent connects to CodeOps-MCP
2. Calls `codeops.initSession(projectId, developerId, environment)`
3. CodeOps returns **Session Context Payload**:
   - **Persona** — full AI behavioral identity for this team
   - **Conventions** — canonical CONVENTIONS.md content
   - **Project Documents** — CLAUDE.md, Architecture.md, Audit.md, OpenAPI.yaml
   - **Ecosystem Context** — from Registry: ports, dependencies, routes, related services
   - **Secret References** — from Vault: credential references for this project/environment
   - **Team Directives** — active team-wide instructions
   - **Recent Session History** — last N sessions on this project (what changed, commit hashes)
   - **Team Discussion** — from Relay: recent messages in the project channel (what the team discussed)
   - **Container Status** — from Fleet: which services are currently running, health status
4. AI operates with full, current context — no manual assembly required

### During Session

- AI makes additional MCP calls: query logs, run API tests, check dependencies, execute SQL, etc.
- All tool calls logged to session record

### Session Completion

1. AI calls `codeops.completeSession(sessionId, results)` with:
   - Commit hash(es)
   - Updated OpenAPI spec (if endpoints changed)
   - Updated audit summary (files changed, tests added, coverage)
   - Session summary (human-readable)
   - Dependency changes
2. CodeOps stores results, updates project documents, notifies team activity feed, and auto-posts session summary to the project's Relay channel
3. Next session on this project (by any developer) starts from updated state

## 9.3 Team Context Management

### Problem Solved

Every developer is an island of configurations. CLAUDE.md, CONVENTIONS.md, audit templates, prompt structures, and coding standards are scattered across repos with no centralized management. Configuration drift is inevitable and invisible. When Developer A updates a convention, Developers B and C never see it.

### Solution

Centralized, cloud-hosted (Postgres) system of record for all team-shared AI development context. Every AI session connects to the same authoritative source via MCP.

### Teams

- Team = group of developers sharing a CodeOps instance (leverages existing CodeOps-Server team model: OWNER, ADMIN, MEMBER, VIEWER)
- Teams share: personas, directives, conventions, project documents, service registrations, port allocations, secrets
- All team data in shared cloud Postgres — accessible from any developer's machine

### Developer Profiles

- Individual identity within team
- Personal preferences layered on top of team defaults
- Session history and activity feed
- API token for MCP connections from local Claude Code

### Scope Model

- **Team scope:** Personas, directives, conventions, project docs, service registrations, port allocations — shared by all
- **Personal scope:** Developer preferences, session history, local environment overrides — per-developer

## 9.4 Persona & Directive Management via MCP

CodeOps-Server already has a working persona and directive system (verified in audit: PersonaApi with 11 methods, DirectiveApi with 11 methods, Persona model with scope/versioning/defaults, Directive model with categories and project assignment). The MCP Gateway extends this existing system to serve AI agents directly.

### Persona Delivery via MCP

- `codeops.getPersona(teamId, agentType)` — fetch the active team persona, including built-in fallback
- Personas already support: SYSTEM (built-in, read-only), TEAM (shared), USER (personal) scopes
- Existing persona assembly order: Built-in → Team override → Team directives → Project directives → Job context = Complete Agent Prompt

### Directive Delivery via MCP

- `codeops.getDirectives(projectId)` — fetch all enabled directives for a project
- Categories already implemented: Architecture, Standards, Conventions, Context, Other
- Project-directive assignment with enable/disable toggle already exists

### Convention Propagation

- Team conventions maintained once in CodeOps, served to every AI session via MCP
- Convention change → immediately available to all sessions, all developers, all projects
- No git commits to 30 repos, no Slack messages about convention updates

## 9.5 Project Document Management

### Documents Managed per Project

- **CLAUDE.md** — project-specific AI instructions
- **CONVENTIONS.md** — coding conventions (team canonical + project extensions)
- **Architecture.md** — system architecture specification
- **Audit.md** — most recent codebase audit results
- **OpenAPI.yaml** — API specification (for backend services)
- **Custom documents** — teams can register additional document types

### Document Lifecycle

- Upload/create manually or via AI session writeback
- Versioning: every update creates new version with timestamp, author (human or AI), commit hash
- Auto-update on session completion — AI sessions write back updated docs
- Staleness detection — flag docs not updated since last N sessions
- Cross-project impact flags — when Project A's API changes, dependent Project B's docs flagged for review

### Document MCP Tools

- `codeops.getProjectDocs(projectId)` — all current documents
- `codeops.getDocument(projectId, docType)` — specific document
- `codeops.getDocumentVersion(projectId, docType, version)` — historical version

## 9.6 Context Staleness Elimination

### Problem Solved

An audit file in a repo is accurate at the moment it's created. After three Claude Code sessions modify the service, the audit is stale. The next developer's AI starts from outdated context, leading to integration failures from stale context, not bad code.

### Solution

- CodeOps is the system of record, not files in repos
- AI sessions write back changes after every session
- Next session starts from **live state**, not stale files
- Document version history shows exactly when and how context changed

## 9.7 Session Writeback & State Tracking

### Session Results Recording

- Commit hash(es) — links session to git history
- Files changed — created, modified, deleted
- Endpoints changed — new, modified, removed
- Test results — tests added, coverage metrics
- Session summary — AI-generated description
- Duration and token usage

### Activity Feed

- Team-wide feed of all session completions across all projects
- "Adam just rebuilt the Gateway's auth module — Service X and Y are affected"
- Filterable by project, developer, time range
- Enables team coordination without meetings

### Session MCP Tools

- `codeops.getSessionHistory(projectId, limit)` — recent sessions
- `codeops.getSessionDetail(sessionId)` — full details
- `codeops.getTeamActivity(since)` — team-wide feed

## 9.8 Registry MCP Tools

- `registry.listServices()` — all services with ports, status, health
- `registry.getService(serviceId)` — full service detail including identity kit
- `registry.registerService(definition)` — register new service, receive allocated identity
- `registry.allocatePort(serviceId, portType)` — allocate from appropriate range
- `registry.getDependencyGraph(serviceId)` — dependency tree
- `registry.getImpactAnalysis(serviceId)` — what breaks if this service changes
- `registry.getRoutes()` — all registered API routes
- `registry.checkRouteConflict(prefix)` — validate before registration
- `registry.generateConfig(serviceId, configType)` — docker-compose, application.yml, etc.
- `registry.getStartupOrder(serviceIds)` — topological sort
- `registry.getEcosystemSnapshot()` — full state of all services

## 9.9 Vault MCP Tools

- `vault.getSecret(path, environment)` — retrieve secret for path and environment
- `vault.listSecrets(pathPrefix)` — list paths under prefix
- `vault.getSecretMetadata(path)` — metadata without actual value
- `vault.transitEncrypt(keyName, plaintext)` — encrypt without storing
- `vault.transitDecrypt(keyName, ciphertext)` — decrypt
- `vault.getServiceCredentials(serviceId, environment)` — all credentials for a service

Write operations restricted by RBAC. AI operates within authenticated developer's permissions.

## 9.10 Logger MCP Tools

- `logger.queryLogs(service, level, timeRange, query)` — search logs
- `logger.getRecentErrors(service, limit)` — recent errors
- `logger.getTraceFlow(correlationId)` — cross-service request trace
- `logger.getMetrics(service, metricName, timeRange)` — metric time-series
- `logger.getServiceHealth(serviceId)` — health from log patterns
- `logger.getAnomalies(service, timeRange)` — detected anomalies

Enables **autonomous debugging**: AI triggers build → Logger catches error → MCP surfaces to agent → agent reads trace → queries DataLens for data state → identifies root cause → patches code.

## 9.11 Courier MCP Tools

- `courier.sendRequest(method, url, headers, body, auth)` — execute HTTP request through Courier proxy (logged, timed, stored in history)
- `courier.runCollection(collectionId, environment, iterations)` — execute collection run
- `courier.getRunResults(runId)` — collection run results
- `courier.importOpenApi(specUrl)` — generate collection from OpenAPI spec
- `courier.getHistory(service, limit)` — recent request history

All requests through Courier proxy = full observability on AI actions.

## 9.12 DataLens MCP Tools

DataLens is client-side only (no server component), so MCP cannot proxy DataLens operations directly. However, AI agents can still interact with databases through the Logger module's database metrics and the Courier module's HTTP testing capabilities. Future consideration: expose a lightweight query execution endpoint in Server for MCP use if demand warrants it.

## 9.13 Relay MCP Tools

- `relay.searchMessages(channelId, query, timeRange)` — search team discussion history
- `relay.getRecentMessages(channelId, limit)` — recent messages in a channel
- `relay.getProjectChannel(projectId)` — get the project's channel and recent discussion
- `relay.postMessage(channelId, content)` — post a message (e.g., session status updates)
- `relay.getThreadReplies(messageId)` — read a discussion thread

Enables AI agents to understand team context: "What did the team decide about the retry strategy?" becomes answerable because Relay conversations are in the central database.

## 9.14 Fleet MCP Tools

- `fleet.listContainers()` — running containers with status, health, ports
- `fleet.startService(serviceId)` — start a container (resolved via Registry)
- `fleet.stopService(serviceId)` — stop a container
- `fleet.restartService(serviceId)` — restart a container
- `fleet.getContainerLogs(serviceId, lines)` — tail container logs
- `fleet.startSolution(solutionId)` — start a group of related services in dependency order
- `fleet.getFleetHealth()` — overall fleet status

Enables **autonomous infrastructure**: AI agent needs to run integration tests → calls `fleet.startSolution("core-platform")` → waits for healthy → runs tests → calls `fleet.stopSolution()`. No human intervention for infrastructure during development sessions.

## 9.15 MCP Security Model

- **Authentication** — JWT from CodeOps-Server. Same tokens used by the Flutter client.
- **Authorization** — RBAC enforced at MCP gateway AND each backend service. AI operates within authenticated developer's permissions.
- **Audit trail** — every MCP tool call logged: who, what, when, which project, which session
- **Secret protection** — Vault ACL policies apply to MCP access identically to UI access
- **Rate limiting** — per-developer, per-session limits
- **Session timeout** — configurable maximum session duration

## MCP Data Model

**8 entities, 8 enums** | **~25 endpoints**
Entities: DeveloperProfile, McpApiToken, McpSession, SessionToolCall, SessionResult, ProjectDocument, ProjectDocumentVersion, ActivityFeedEntry
Enums: SessionStatus, DocumentType, ActivityType, ToolCallStatus, McpTransport, Environment, AuthorType, TokenStatus

---

# CROSS-SERVICE INTEGRATION

All of these integrations are internal Java method calls within CodeOps-Server (except Vault which requires HTTP). No network overhead, no serialization, no service discovery.

## Registry → All Modules
Central catalog. All modules access Registry for service discovery, ports, dependencies.

## Vault → All Modules (HTTP)
Stores secrets used by DataLens (DB passwords via client "Fetch from Vault"), Courier (API keys), Logger (webhook secrets), Fleet (container environment variables).

## Logger → All Modules
Receives structured logs. All services emit logs tagged with Registry service identity. Fleet pipes container logs to Logger for persistent storage.

## Relay → All Modules
**PlatformEventService** is the integration hub. Every module fires events to Relay:
- Core: project created/archived
- Registry: service registered/deregistered
- Vault: secret rotated, policy changed
- Logger: alert fired, anomaly detected
- Courier: collection run failed
- Fleet: container crashed, health failure, crash loop detected
- MCP: session completed (auto-posts summary to project channel)

## Fleet → Registry + Vault
Fleet reads service definitions from Registry (ports, dependencies, startup order) and fetches container credentials from Vault. Health failures fire platform events to Relay.

## Scribe → All Frontend Modules
Shared `ScribeEditor` Flutter widget consumed by Courier (scripts), DataLens (SQL), Logger (queries), Registry (configs), Vault (secret editing), Relay (message composer), MCP (document editing).

## MCP → All Modules
Aggregates all modules into unified MCP tool surface for AI agents. Direct `@Autowired` injection to Registry, Logger, Courier, Relay, Fleet. HTTP only to Vault.

## Registry + Vault + Relay + Fleet → MCP Session Context
Session initialization pulls: service identity (Registry), credentials (Vault), team discussion (Relay), container status (Fleet), recent errors (Logger), test results (Courier).

## Logger + MCP → Autonomous Debugging
Logger surfaces errors to AI agents via MCP for closed-loop debug cycles.

## Courier + MCP → AI HTTP Testing
AI executes and validates API requests through Courier with full observability.

## Fleet + MCP → Autonomous Infrastructure
AI starts/stops containers via Fleet during sessions for integration testing without human intervention.

## Relay + MCP → Team Context for AI
AI searches Relay message history to understand team decisions and ongoing discussions.

## CodeOps-Server ← All Modules
Single Spring Boot application. All modules share: auth (JWT), RBAC, user profiles, team membership, personas, directives, database, exception handling, request correlation, logging infrastructure.

---

# INTEGRATION & POLISH (Complete)

## Unified Dashboard
- All module health at a glance on existing CodeOps-Client home page
- Recent activity across all modules
- Quick actions: register service, create secret, open query, send request, start session, open channel
- MCP team activity feed
- Relay unread summary
- Fleet container status overview

## Cross-Module Navigation
- Click service in Registry → open in Courier (test API) or DataLens (explore database) or Fleet (start/stop container)
- Click log entry's service name → navigate to Registry detail
- Click secret reference → open in Vault
- Click MCP session project → navigate to project page
- Click Fleet container log → open in Logger for persistent search
- Click Relay platform event → navigate to source module (audit, alert, session, registration)
- DataLens connection → "Fetch from Vault" for credentials
- Registry service → DataLens "Explore Database"

## Global Search
- Single search bar (Ctrl+K): search across secrets, logs, collections, queries, services, sessions, documents, tables, messages
- Results grouped by module with icons
- Click → navigate to result

## Master Docker Compose
- Single `docker-compose.yml` in CodeOps-Server: PostgreSQL (Server :5432), PostgreSQL (Vault :5433), Redis (:6379), Kafka (:9092) + Zookeeper (:2181)
- Startup/stop/reset scripts in `scripts/`
- Only 2 Postgres instances

## Master Startup Script
- Health-check each service, ordered startup
- Two services: `mvn spring-boot:run` for Server, `mvn spring-boot:run` for Vault

## End-to-End Integration Tests
- Cross-module workflow tests: register service → create secrets → send API request → verify logs → check Relay notification → start container via Fleet → check MCP context includes all data
- Testcontainers-based

---

# DEPLOYMENT

## Local Development

```bash
# Start infrastructure
cd ~/Documents/Github/CodeOps-Server
./scripts/start-infra.sh
# Starts: Postgres:5432 (Server), Postgres:5433 (Vault),
#         Redis:6379, Kafka:9092, Zookeeper:2181

# Start backend services (only 2)
cd ~/Documents/Github/CodeOps-Server && mvn spring-boot:run      # :8095 (all modules)
cd ~/Documents/Github/CodeOps-Vault && mvn spring-boot:run       # :8097

# Start Flutter desktop client
cd ~/Documents/Github/CodeOps-Client && flutter run -d macos     # Native desktop
```

## Cloud Deployment
- Cloud Postgres (RDS) — one for Server, one for Vault
- Two containers total via existing Dockerfile pattern (eclipse-temurin:21-jre-alpine, non-root user)
- Same JWT authentication, same RBAC — nothing changes local to cloud
- CodeOps-Server already designed for Docker → ECS Fargate deployment

---

# METRICS

| Metric | Value |
|--------|-------|
| Platform status | **CodeOps v1.0 — COMPLETE** |
| Backend services | **2** (CodeOps-Server + CodeOps-Vault) |
| Server modules | **7** (core, registry, logger, courier, relay, fleet, mcp) — all ✅ |
| Server entities | **114** entity classes across **~84 tables** |
| Server endpoints | **~526** |
| Server source files | **905** | Server test files: **243** | Server tests: **~3,500+** |
| Frontend modules | **12** — all ✅ (Registry, Vault, Logger, Courier, DataLens, Relay, Fleet, Scribe, MCP, Dashboard, Global Search, Preferences) |
| Frontend screens | **90+** across **85+ routes** |
| Frontend source files | **1,200+** | Frontend test files: **512+** | Frontend tests: **~6,000+** |
| Total tasks delivered | **115 / 115** across **13 phases** |
| Total tests (platform) | **~9,500+** (server + client) |
| Enterprise SaaS replaced | **8 products** + dev tools |
| Annual cost replaced | **$620K–2.65M+** |
| Novel capability (MCP) | **No market equivalent** |
| Docker containers (dev) | **2 apps + 4 infra** (Server + Vault + 2×Postgres + Redis + Kafka) |
| Postgres instances | **2** (Server + Vault) |
| Active repositories | **3** (Server, Vault, Client) under AI-CodeOps GitHub org |
| API methods consumed by Client | **~420** |
