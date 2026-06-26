# Changelog

All notable changes to the **Antigravity Developer Stack** will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [1.3.0] - 2026-06-26

### Added
- `tools-automation/linear-expert` — Adapted from Claude-specific scripts to a generic REST/GraphQL workflow.
- `tools-automation/docs-architect` — Deep technical manuals compilation from codebase analysis.
- `languages-standards/nodejs-best-practices` — Layered architecture, runtime selection, and async principles for Node.js.
- `languages-standards/software-architecture` — General code style rules, naming conventions, and library-first development standards.
- `languages-standards/commit` — Conventional Commits formatting, git logs, and hybrid orchestration (consolidated with commit-formatter).
- `backend-infra/security-audit` — Focused backend security threat modeling, multi-tenancy RLS audits, and API authentication guards verification.

- `ai-agents/ai-agents-architect` — Master loops, memory architectures, and multi-agent coordination.
- `strategy-architecture/architecture` — System design and ADR templates.
- `strategy-architecture/architecture-patterns` — Hexagonal, Clean, and DDD patterns.
- `frontend-ui/accessibility-audit` — Comprehensive WCAG compliance auditing, keyboard navigation, and screen reader verification workflows.
- `frontend-ui/antigravity-design-expert` — Core UI/UX engineering skill for building highly interactive, spatial, weightless, and glassmorphism-based web interfaces using GSAP and 3D CSS.
- `tools-automation/design-md` — Analyze Stitch projects and synthesize semantic design systems into DESIGN.md files.
- `frontend-ui/design-spells` — Curated micro-interactions, Easter eggs, and design details that add magic and personality to websites and apps.
- `strategy-architecture/design-orchestration` — Meta-skill to orchestrate design workflows through brainstorming, multi-agent review, and readiness checks.
- `strategy-architecture/antigravity-workflows` — Orchestrate multiple Antigravity skills through guided workflows for SaaS MVP, security audits, AI agents, and browser QA.
- `frontend-ui/ui-a11y` — StyleSeed-based component accessibility auditing, WCAG 2.2 AA verification, and mobile-first autofixes.
- `frontend-ui/wcag-audit-patterns` — Comprehensive guide to auditing web content against WCAG 2.2 guidelines with actionable remediation strategies.
- `frontend-ui/accesslint-audit` — Find and fix WCAG 2.2 accessibility issues using live DOM CDP or static HTML string audits.
- `frontend-ui/web-design-guidelines` — Code compliance verification against Vercel's Web Interface Guidelines.
- `frontend-ui/web-artifacts-builder` — Bundling self-contained React/Tailwind/shadcn UIs as interactive documentation pages for Antigravity.
- `frontend-ui/ui-ux-designer` — User research methodologies, wireframing, design systems (atomic design), and design tokens for cross-platform layouts.
- `frontend-ui/dashboard-design` — Implementation guide and DNA for analytics-focused grids, modular widgets, and responsive layouts.
- `product-building/vibecode-production-qa-validator` — 13-phase QA launch-readiness validator for fullstack Next.js applications covering SEO, Auth, and performance.
- `product-building/close-epic` — Ritual de consolidación, versionado y cierre de bloques de desarrollo estratégico (Epics) en Git.
- `product-building/copilot` — Orquestador universal de workflow y checklist pre-flight obligatorio para gobernar las tareas.
- `tools-automation/analyze-project` — Forensic root cause analyzer for Antigravity sessions to classify scope deltas, rework patterns, and hotspots.
- `ai-agents/prompt-engineer` — Transmute raw prompts into structured prompt frameworks (RTF, RISEN, Chain of Thought, etc.) to optimize AI output.
- `tools-automation/github-workflow-automation` — AI-assisted GitHub Action setups, issue triage, and smart test select patterns.
- `fullstack/vibe-code-cleanup` — Safe production cleanup and hardening for AI/vibe-coded fullstack apps.
- `growth/linkedin-profile-optimizer` — Audit and optimize LinkedIn profile positioning for authority and SEO.
- `growth/social-post-writer-seo` — Platform-optimized social media content generation.
- `skill-authoring/writing-great-skills` — Vocabulary, information hierarchy, and principles for writing predictable skills.
- `tools-automation/github-automation` — Automate GitHub repositories, issues, PRs, and workflows via Rube MCP (Composio).
- `tools-automation/github-actions-templates` — Production-ready GitHub Actions workflow patterns for testing, building, and deploying.
- `tools-automation/git-pr-review` — Generate a concise and structured PR description from commit history with minimal token usage.
- `tools-automation/n8n-code-javascript` — Write custom JavaScript inside n8n Code nodes (managing arrays, dates, and nested webhook bodies).
- `tools-automation/n8n-workflow-patterns` — High-level architectural design patterns for n8n (webhooks, API pipelines, db sync, and scheduled jobs).
- `tools-automation/docs-sync` — Surgical documentation synchronization upon epic/feature closure.


### Changed
- `languages-standards/testing-patterns` — Migrated completely from Jest to **Vitest** mocking and assertions.
- `tools-automation/documentation-expert` — Consolidated with `doc-writer` to cover project knowledge bases (`.knowledge/` directory).
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
