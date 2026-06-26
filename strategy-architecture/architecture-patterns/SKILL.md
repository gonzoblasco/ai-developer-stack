---
name: architecture-patterns
description: "Master proven backend architecture patterns including Clean Architecture, Hexagonal Architecture, and Domain-Driven Design to build maintainable, testable, and scalable systems."
risk: safe
source: community
date_added: "2026-06-26"
---

# Architecture Patterns

Master proven backend architecture patterns including Clean Architecture, Hexagonal Architecture, and Domain-Driven Design to build maintainable, testable, and scalable systems.

## Use this skill when

- Designing new backend systems from scratch.
- Refactoring monolithic applications for better maintainability.
- Establishing architecture standards for your team.
- Migrating from tightly coupled to loosely coupled architectures.
- Implementing domain-driven design principles.
- Creating testable and mockable codebases.
- Planning microservices decomposition.

## Do not use this skill when

- You only need small, localized refactors.
- The system is primarily frontend with no backend architecture changes.
- You need implementation details without architectural design.

## Core Architectural Guidelines

1. **Clarify Domain Boundaries**: Establish clear bounded contexts, business constraints, and scalability targets before choosing an architectural pattern.
2. **Decouple Business Logic**: Separate core business rules (entities, use cases) from external details (databases, HTTP frameworks, third-party APIs) using interfaces/ports and adapters.
3. **Establish Dependency Rules**: Dependencies should only point inwards toward the core domain. Outer layers (frameworks, drivers) can depend on inner layers, but inner layers must never depend directly on outer layers.
4. **Failure-Resilient Workflows**: For processes requiring multiple steps that must survive failures (e.g., payments, order fulfillment), design them around durable execution patterns or idempotent message-handling interfaces.

## 🔗 Related Skills

| Skill | Use For | Path |
|-------|---------|------|
| `architecture` | General architecture decisions | [architecture](file:///Users/gonzoblasco/.gemini/config/skills/strategy-architecture/architecture/SKILL.md) |
| `saas-multi-tenant` | Designing multi-tenant architectures | [saas-multi-tenant](file:///Users/gonzoblasco/.gemini/config/skills/strategy-architecture/saas-multi-tenant/SKILL.md) |
| `senior-architect` | System design & diagram tools | [senior-architect](file:///Users/gonzoblasco/.gemini/config/skills/strategy-architecture/senior-architect/SKILL.md) |

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
