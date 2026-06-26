---
name: architecture
description: "Architectural decision-making framework. Requirements analysis, trade-off evaluation, ADR documentation. Use when making architecture decisions or analyzing system design."
risk: safe
source: community
date_added: "2026-06-26"
---

# Architecture Decision Framework

> "Requirements drive architecture. Trade-offs inform decisions. ADRs capture rationale."

---

## 🔗 Related Skills

| Skill | Use For | Path |
|-------|---------|------|
| `database-design` | Database schema design | [database-design](file:///Users/gonzoblasco/.gemini/config/skills/backend-infra/database-design/SKILL.md) |
| `api-patterns` | API design patterns | [api-patterns](file:///Users/gonzoblasco/.gemini/config/skills/backend-infra/api-patterns/SKILL.md) |
| `senior-architect` | System design & tooling | [senior-architect](file:///Users/gonzoblasco/.gemini/config/skills/strategy-architecture/senior-architect/SKILL.md) |

---

## Core Principles

**"Simplicity is the ultimate sophistication."**

- **Start Simple**: Implement the simplest working solution first.
- **De-risk Early**: Identify technical risks and prototype those specific areas first.
- **Trade-off Evaluation**: Every decision has a trade-off. Explicitly document *why* a choice was made and what was sacrificed (e.g., speed vs. consistency).
- **Avoid Over-Engineering**: Add complex architectural patterns only when proven necessary.

---

## Architecture Decision Record (ADR) Template

When documenting key architectural decisions, use the following structure:

```markdown
# ADR-[Number]: [Title of Decision]

## Context
Describe the technical context, requirements, constraints, and the problem being solved.

## Decision
Explain the chosen path clearly, specifying any frameworks, patterns, or tools selected.

## Consequences
Detail the outcomes of this decision, both positive and negative (e.g., increased complexity, improved latency, maintenance overhead).
```

---

## Validation Checklist

Before finalizing system architecture:

- [ ] Requirements and constraints are clearly understood and documented.
- [ ] At least one alternative approach has been considered and evaluated.
- [ ] Each major technical decision has a clear trade-off analysis.
- [ ] Architectural decisions are documented using ADRs.
- [ ] The team's expertise aligns with the selected technology stack.

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
