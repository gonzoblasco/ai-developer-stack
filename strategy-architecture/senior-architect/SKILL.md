---
name: senior-architect
description: "Complete toolkit for senior architects: architecture diagrams, project analysis, dependency audits, system design workflows, and tech decision frameworks. Use when designing systems, evaluating tech stacks, or making architecture trade-offs."
risk: critical
source: community
date_added: "2026-02-27"
---

# Senior Architect

Complete toolkit for senior architects with modern tools, automated scripts, and best practices for designing scalable, maintainable systems.

## When to Use

- Designing system architecture and making technical decisions
- Creating or reviewing architecture diagrams (Mermaid)
- Evaluating and selecting tech stacks
- Analyzing project dependencies and health
- Documenting Architecture Decision Records (ADRs)
- Assessing scalability, performance, or security trade-offs

## Quick Start

### Core Scripts

```bash
# 1. Generate architecture diagrams (Mermaid) from codebase
npx tsx scripts/architecture_diagram_generator.ts <project-path> --output diagram.mmd

# 2. Audit project health against architectural best practices
npx tsx scripts/project_architect.ts <target-path> [--verbose]

# 3. Analyze dependencies (package.json, lock file) and report metrics
npx tsx scripts/dependency_analyzer.ts <project-path> --json
```

---

## Core Capabilities

### 1. Architecture Diagram Generator

Generates Mermaid JS diagrams from your codebase structure.

**Features:**
- Automated scaffolding from live codebase
- Configurable diagram templates (C4, flowchart, sequence)
- Best practices built-in
- Quality checks on generated output

**Usage:**
```bash
npx tsx scripts/architecture_diagram_generator.ts <project-path> [options]
# Options:
#   --output <file.mmd>    Output file path
#   --style c4|flow|seq    Diagram style (default: c4)
#   --depth <n>            Directory depth to analyze
```

### 2. Project Architect (Health Linter)

Checks project health against architectural best practices — verifies presence of README, Dockerfile, .gitignore, security headers, test coverage config, and more.

**Features:**
- Deep structural analysis
- Performance metrics
- Concrete recommendations
- Automated fix suggestions

**Usage:**
```bash
npx tsx scripts/project_architect.ts <target-path> [--verbose]
```

### 3. Dependency Analyzer

Analyzes project dependencies (package.json, requirements.txt, go.mod) and reports metrics: outdated packages, security advisories, circular dependencies, and bundle impact.

**Features:**
- Expert-level dependency mapping
- Custom vulnerability checks
- Integration with npm audit / pip audit
- Production-grade output (JSON/text)

**Usage:**
```bash
npx tsx scripts/dependency_analyzer.ts <project-path> [--json] [--fix]
```

---

## Reference Documentation

Detailed guides are available in the `references/` directory:

| Reference | Contents |
|---|---|
| [Architecture Patterns](references/architecture_patterns.md) | Hexagonal, Clean, DDD, CQRS, Event Sourcing patterns with code examples |
| [System Design Workflows](references/system_design_workflows.md) | Step-by-step processes, capacity planning, performance tuning |
| [Tech Decision Guide](references/tech_decision_guide.md) | Stack selection criteria, security, scalability, integration patterns |

---

## Tech Stack Coverage

| Layer | Technologies |
|---|---|
| **Languages** | TypeScript, JavaScript (Node.js — FullStack) |
| **Frontend** | React, Next.js, React Native |
| **Backend** | Node.js, NestJS, Express, tRPC, GraphQL, REST APIs |
| **Database** | PostgreSQL, Prisma, NeonDB, Supabase, Redis |
| **DevOps** | Docker, Kubernetes, Terraform, GitHub Actions, CircleCI |
| **Cloud** | AWS, GCP, Azure |

---

## Architecture Decision Framework

### Trade-off Analysis Template

When evaluating any architectural decision, use this structure:

```
## Decision: [title]

### Context
What problem are we solving? What constraints exist?

### Options Considered
| Option | Pros | Cons | Complexity |
|--------|------|------|------------|
| A      |      |      |            |
| B      |      |      |            |

### Decision
Chosen option and rationale.

### Consequences
What becomes easier? What becomes harder?
```

### Scalability Checklist
- [ ] Stateless services (horizontal scaling possible)
- [ ] Database connection pooling configured
- [ ] Caching layer defined (Redis / CDN / in-memory)
- [ ] Async processing for long-running tasks
- [ ] Rate limiting and circuit breakers in place
- [ ] Observability: logs, metrics, traces wired up

---

## Development Workflow

### 1. Analyze Current State
```bash
npx tsx scripts/project_architect.ts .
npx tsx scripts/dependency_analyzer.ts . --json
```

### 2. Visualize Structure
```bash
npx tsx scripts/architecture_diagram_generator.ts . --output architecture.mmd
```

### 3. Plan Changes
Reference `references/architecture_patterns.md` and `references/tech_decision_guide.md`.

### 4. Quality Checks
```bash
npm run test
npm run lint
npm run build
```

### 5. Deploy
```bash
docker build -t app:latest .
docker-compose up -d
kubectl apply -f k8s/
```

---

## Best Practices Summary

### Code Quality
- Follow established patterns (Hexagonal / Clean Architecture)
- Write comprehensive tests (unit + integration + E2E)
- Document decisions with ADRs
- Code review gate before merging

### Performance
- Measure before optimizing (profiling first)
- Use appropriate caching at the right layer
- Optimize critical paths (N+1 queries, blocking I/O)
- Monitor in production with APM

### Security
- Validate all inputs (Zod / Valibot at API boundary)
- Use parameterized queries (never string interpolation)
- Implement proper authentication (JWT + refresh + rotation)
- Keep dependencies updated (weekly `npm audit`)

### Maintainability
- Single Responsibility at every layer
- Consistent naming conventions across the team
- Architecture diagrams updated on each significant change
- Runbooks for all production operations

---

## Troubleshooting

Common issues and resolutions are documented in `references/tech_decision_guide.md`.

When stuck:
1. Review reference documentation
2. Check script output messages and logs
3. Consult official tech stack documentation
4. Review error logs in observability dashboards

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- `risk: critical` — decisions made here affect system-wide architecture. Validate with the team before applying.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
