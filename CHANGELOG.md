# Changelog

All notable changes to the **Antigravity Developer Stack** will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [1.3.0] - 2026-06-26

### Added
- `tools-automation/linear-expert` — Adapted from Claude-specific scripts to a generic REST/GraphQL workflow.
- `tools-automation/docs-architect` — Deep technical manuals compilation from codebase analysis.
- `languages-standards/nodejs-best-practices` — Layered architecture, runtime selection, and async principles for Node.js.
- `ai-agents/ai-agents-architect` — Master loops, memory architectures, and multi-agent coordination.
- `strategy-architecture/architecture` — System design and ADR templates.
- `strategy-architecture/architecture-patterns` — Hexagonal, Clean, and DDD patterns.

### Changed
- `languages-standards/testing-patterns` — Migrated completely from Jest to **Vitest** mocking and assertions.
- Updated all folder-level playbooks (`README.md` files) and the root `README.md`.

### Removed / Deprecated
- `backend-infra/backend-expert` — Consolidated into `nodejs-best-practices` and `database-design`.
- `strategy-architecture/planning-expert` — Deprecated in favor of Antigravity's native planning mode (`task.md` / `implementation_plan.md`).
- `product-building/writing-plans` — Deprecated/deleted in favor of `plan-writing`.
- Removed temporary/legacy/test skills: `add-about-page`, `add-health-endpoint`, `react-exam-copilot`, and `react-frontend-patterns`.

---

## [1.2.0] - 2026-02-24

### Added

- Nueva categoría **`product-building`** — skills orientadas al ciclo completo de vida de un producto usando plataformas low-code/no-code + AI
- `lovable-saas-builder` skill — Workflow completo para construir SaaS B2B con Lovable Cloud + Supabase
  - Prompts estructurados para Design System, Auth, CRUD, Edge Functions e integraciones de pago
  - Patrones de Edge Functions reutilizables (OAuth, webhooks, AI, pagos)
  - Guía de deployment y go-live checklist
  - Basado en patrones extraídos del proyecto SoporteML

### Changed

- `README.md`: agregada sección "Product Building Playbook" y entrada en el Capability Map

---

## [1.1.0] - 2026-02-06

### Added

- `react-exam-copilot` skill - Senior React exam & coding challenge assistant
  - Training mode with full solutions and explanations
  - Exam mode with guided hints (no direct answers)
  - Checklists: accessibility, performance, code-review
  - Patterns: custom hooks, compound components, error boundaries, data fetching
  - Templates: component, custom hook, test setup, error boundary

### Changed

- Updated `README.md` to include `react-exam-copilot` in Frontend & UI/UX section
- Updated `frontend-ui/README.md` with skill in Phase 3 and Skill Index table

---

## [1.0.0] - 2026-01-29

### Added

- Initial release of the Antigravity Developer Stack
- **AI & Autonomous Agents**: autonomous-agent-expert, agent-tool-builder, llm-app-patterns, mcp-builder, prompt-mastery, rag-expert, chatgpt-project-architect, meta-skill-antigravity
- **Strategy & Architecture**: senior-architect, planning-expert, brainstorming, pricing-strategy, marketing-ideas, kaizen, app-builder
- **Backend & Infrastructure**: backend-expert, nestjs-expert, api-patterns, database-design, postgres-best-practices, docker-expert, mercadolibre-api
- **Frontend & UI/UX**: frontend-dev-guidelines, react-frontend-patterns, react-ui-patterns, react-migration-16-to-19, redux-migration-rtk-zustand, nextjs-best-practices, tailwind-patterns, ui-ux-pro-max
- **Tools & Automation**: browser-automation-expert, n8n-workflow-builder, pdf-official
- **Languages & Standards**: typescript-expert, testing-patterns
- Engineering Playbooks for each domain
