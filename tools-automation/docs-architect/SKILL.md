---
name: docs-architect
description: "Creates comprehensive technical documentation from existing codebases. Analyzes architecture, design patterns, and implementation details to produce long-form technical manuals and ebooks."
risk: safe
source: community
date_added: "2026-06-26"
---

# Docs Architect

Creates comprehensive technical documentation from existing codebases. Analyzes architecture, design patterns, and implementation details to produce long-form technical manuals and ebooks.

## Use this skill when

- Generating comprehensive technical manuals, READMEs, or architecture guides.
- Onboarding new developers and documenting system flow.
- Analyzing existing codebases to document design decisions and data schemas.

## Do not use this skill when

- Writing user manuals, marketing content, or copywriting.
- Generating basic automated API code references (e.g. Swagger) without design rationale.

## Core Documentation Process

1. **Discovery Phase**:
   - Analyze codebase structure, entry points, and dependencies.
   - Map core data models, database schemas, and external API integrations.
   - Extract design patterns and architectural decisions.

2. **Structuring Phase**:
   - Establish a progressive disclosure hierarchy (general system overview leading to specific component modules).
   - Plan out visual diagrams (e.g., flowcharts, database relationships, sequence flows).

3. **Writing Phase**:
   - Document both the **what** and the **why** behind design decisions.
   - Embed exact code references or snippets with walk-through explanations.

## Key Sections to Include

1. **Executive Summary**: One-page overview for stakeholders.
2. **Architecture Overview**: System boundaries, component interactions, and layers.
3. **Design Decisions**: Rationale behind architectural choices (e.g., ADRs).
4. **Core Components**: Deep dive into each major module or service.
5. **Data Models**: Schema design and data flow documentation.
6. **Integration Points**: API routes, event buses, and external dependencies.
7. **Security Model**: Authentication, authorization, and data protection rules.

## Output Format

Generate documentation in Markdown format with:
- Clear, nested heading hierarchy.
- Code blocks with appropriate syntax highlighting.
- Tables for structured configuration, database schemas, or API endpoints.
- Relative links to relevant codebase files in the format `[filename](file:///path/to/file#lines)`.

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
