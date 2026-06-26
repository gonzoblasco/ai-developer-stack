---
name: software-architecture
description: "Guide for quality-focused software development and coding standards. Focuses on code style rules, library-first approach, naming conventions, and separation of concerns."
risk: safe
source: community
date_added: "2026-06-26"
---

# Software Architecture & Coding Standards

This skill provides concrete style and architectural rules to keep codebases clean, maintainable, and robust.

---

## 🎨 Code Style Rules

### General Principles
- **Early Return Pattern**: Use early returns instead of nested `if` conditions to improve readability.
- **Decomposition**: Keep functions focused and under 50 lines. If a file exceeds 200 lines of code, split it into smaller, logically focused modules/files.
- **Arrow Functions**: Prefer arrow functions (`const myFn = () => {}`) over function declarations when possible, especially in React components or callbacks.

---

## 📦 Best Practices

### Library-First Approach
- **Search Before Writing**: Always search for existing, well-tested solutions before writing custom utility code.
  - Check `npm` or language registries for existing libraries (e.g., use `cockatiel` instead of writing custom retry loops).
  - Evaluate SaaS, BaaS (e.g., Supabase/Auth0 instead of custom auth), or external APIs.
- **When Custom Code is Justified**:
  - Domain-specific business logic.
  - Performance-critical hot paths.
  - Security-sensitive features requiring absolute internal control.

### Naming Conventions
- **Avoid Generic Dumping Grounds**: Never create files or folders named `utils`, `helpers`, `common`, or `shared`. They attract unrelated, disorganized code.
- **Use Domain-Specific Names**: Name files, classes, and helper folders after their specific domain purpose (e.g., `OrderCalculator.ts`, `UserAuthenticator.ts`, `InvoiceGenerator.ts`).

### Separation of Concerns
- **Separate Layers**: Keep business logic completely separate from UI view components and HTTP routing controllers.
- **Database Abstraction**: Never call ORMs or query builders directly inside route handlers. Delegate to a repository layer.

---

## 🚫 Anti-Patterns to Avoid

- **Not Invented Here (NIH) Syndrome**: Rebuilding auth, form validation, state management, or networking logic that is already solved by industry-standard libraries.
- **Poor Layouts**: Mixing data fetching, business rule validations, and UI rendering inside a single React component or route file.

---

## 🔗 Related Skills

| Skill | Use For | Path |
|-------|---------|------|
| `clean-code` | Uncle Bob's general naming and formatting guidelines | [clean-code](file:///Users/gonzoblasco/.gemini/config/skills/languages-standards/clean-code/SKILL.md) |
| `architecture-patterns` | Clean Architecture, Hexagonal, and DDD principles | [architecture-patterns](file:///Users/gonzoblasco/.gemini/config/skills/strategy-architecture/architecture-patterns/SKILL.md) |
| `nodejs-best-practices` | Framework selection and runtime considerations | [nodejs-best-practices](file:///Users/gonzoblasco/.gemini/config/skills/languages-standards/nodejs-best-practices/SKILL.md) |

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
