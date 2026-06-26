# Changelog

Todos los cambios notables del **Antigravity Developer Stack** quedan documentados en este archivo.

El formato está basado en [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [1.3.0] - 2026-06-26

### Agregado
- `tools-automation/linear-expert` — Adaptado desde scripts específicos de Claude a un workflow genérico REST/GraphQL.
- `tools-automation/docs-architect` — Compilación de manuales técnicos profundos desde análisis de codebase.
- `languages-standards/nodejs-best-practices` — Arquitectura en capas, selección de runtime y principios async para Node.js.
- `languages-standards/software-architecture` — Reglas generales de estilo de código, convenciones de naming y estándares de desarrollo library-first.
- `languages-standards/commit` — Formato Conventional Commits, git logs y orquestación híbrida (consolidado con commit-formatter).
- `backend-infra/security-audit` — Threat modeling de seguridad de backend, auditorías RLS multi-tenancy y verificación de guards de autenticación de API.

- `ai-agents/ai-agents-architect` — Loops maestros, arquitecturas de memoria y coordinación multi-agente.
- `strategy-architecture/architecture` — Diseño de sistemas y templates ADR.
- `strategy-architecture/architecture-patterns` — Patrones Hexagonal, Clean y DDD.
- `frontend-ui/accessibility-audit` — Auditoría completa de cumplimiento WCAG, navegación por teclado y workflows de verificación de screen readers.
- `frontend-ui/antigravity-design-expert` — Skill core de ingeniería UI/UX para construir interfaces web altamente interactivas, espaciales, sin peso y basadas en glassmorphism usando GSAP y CSS 3D.
- `tools-automation/design-md` — Análisis de proyectos Stitch y síntesis de design systems semánticos en archivos DESIGN.md.
- `frontend-ui/design-spells` — Micro-interacciones curadas, Easter eggs y detalles de diseño que agregan magia y personalidad a sitios y apps.
- `strategy-architecture/design-orchestration` — Meta-skill para orquestar workflows de diseño a través de brainstorming, revisiones multi-agente y checks de readiness.
- `strategy-architecture/antigravity-workflows` — Orquestación de múltiples skills Antigravity a través de workflows guiados para SaaS MVP, auditorías de seguridad, agentes de IA y QA de browser.
- `frontend-ui/ui-a11y` — Auditoría de accesibilidad de componentes basada en StyleSeed, verificación WCAG 2.2 AA y autofixes mobile-first.
- `frontend-ui/wcag-audit-patterns` — Guía completa para auditar contenido web contra lineamientos WCAG 2.2 con estrategias de remediación accionables.
- `frontend-ui/accesslint-audit` — Encontrar y corregir problemas de accesibilidad WCAG 2.2 usando auditorías de DOM en vivo (CDP) o de strings HTML estáticos.
- `frontend-ui/web-design-guidelines` — Verificación de cumplimiento de código contra los Web Interface Guidelines de Vercel.
- `frontend-ui/web-artifacts-builder` — Empaquetado de UIs autocontenidas (React/Tailwind/shadcn) como páginas de documentación interactiva para Antigravity.
- `frontend-ui/ui-ux-designer` — Metodologías de user research, wireframing, design systems (atomic design) y design tokens para layouts cross-platform.
- `frontend-ui/dashboard-design` — Guía de implementación y ADN para grids enfocados en analytics, widgets modulares y layouts responsivos.
- `frontend-ui/material-design` — Guías de implementación de Material Design 3 para Web (CSS), iOS (SwiftUI), Android (Jetpack Compose), Flutter y React Native.
- `frontend-ui/react-best-practices` — Guía de rendimiento de React y Next.js mantenida por Vercel: waterfalls, tamaño de bundle, caché y renderizado.
- `frontend-ui/react-state-management` — Guía de patrones modernos de gestión de estado en React: estado local, server state y stores globales (Zustand, RTK, Jotai).
- `frontend-ui/senior-frontend` — Scripts y patrones de scaffolding, generación de componentes y analizador de bundle para React/Next.js.
- `frontend-ui/threejs-fundamentals` — Setup de escenas 3D WebGL/WebGPU, configuraciones de cámara, features del renderer y utilidades básicas de Matemática/Coordenadas.

- `product-building/vibecode-production-qa-validator` — Validador de launch-readiness QA de 13 fases para aplicaciones Next.js fullstack cubriendo SEO, Auth y rendimiento.
- `product-building/new-task` — Inicializar una nueva task del epic activo, incluyendo lectura de contexto, precondiciones de branch y validación de entorno.
- `product-building/pr` — Crear pull request con descripción estructurada, correr revisión local y mergear automáticamente vía API.
- `product-building/close-epic` — Ritual de consolidación, versionado y cierre de bloques de desarrollo estratégico (Epics) en Git.
- `product-building/micro-saas-launcher` — Lanzamiento rápido de MVPs y SaaS con enfoque Indie Hacker (validación de idea, pricing, launch, churn, onboarding).
- `product-building/product-manager` — Agente PM Senior: 6 dominios de conocimiento, 30+ frameworks, 12 templates, 32 métricas SaaS con fórmulas (MIT / Digidai).
- `product-building/product-manager-toolkit` — Toolkit práctico de PM: priorizador RICE, analizador NLP de entrevistas, templates de PRD, frameworks de discovery y MoSCoW.
- `product-building/copilot` — Orquestador universal de workflow y checklist pre-flight obligatorio para gobernar las tareas.

- `tools-automation/analyze-project` — Analizador forense de causa raíz para sesiones de Antigravity: clasifica deltas de scope, patrones de rework y hotspots.
- `ai-agents/prompt-engineer` — Transmuta prompts crudos en frameworks de prompts estructurados (RTF, RISEN, Chain of Thought, etc.) para optimizar el output de IA.
- `tools-automation/github-workflow-automation` — Setups de GitHub Actions asistidos por IA, triage de issues y patrones de selección inteligente de tests.
- `tools-automation/pr-review` — Linter cognitivo pre-merge que verifica seguridad, convenciones, corrección y rendimiento sobre diffs de branch.

- `fullstack/vibe-code-cleanup` — Limpieza segura y endurecimiento de producción para apps fullstack generadas con IA/vibe coding.
- `fullstack/refactor` — Refactoriza código existente para mejorar legibilidad y reducir duplicación sin alterar comportamiento.

- `growth/linkedin-profile-optimizer` — Auditoría y optimización del posicionamiento del perfil de LinkedIn para autoridad y SEO.
- `growth/social-post-writer-seo` — Generación de contenido para redes sociales optimizado por plataforma.
- `skill-authoring/writing-great-skills` — Vocabulario, jerarquía de información y principios para escribir skills predecibles.
- `tools-automation/github-automation` — Automatizar repositorios, issues, PRs y workflows de GitHub vía Rube MCP (Composio).
- `tools-automation/github-actions-templates` — Patrones de workflow de GitHub Actions listos para producción: testing, build y deploy.
- `tools-automation/git-pr-review` — Generar una descripción de PR concisa y estructurada desde el historial de commits con uso mínimo de tokens.
- `tools-automation/n8n-code-javascript` — Escribir JavaScript personalizado dentro de nodos Code de n8n (manejo de arrays, fechas y cuerpos de webhooks anidados).
- `tools-automation/n8n-workflow-patterns` — Patrones de diseño arquitectónico de alto nivel para n8n (webhooks, pipelines de API, sincronización de BD y jobs programados).
- `tools-automation/docs-sync` — Sincronización quirúrgica de documentación al cerrar epics/features.
- `tools-automation/readme` — Guía de escritor técnico experto para crear archivos README de proyectos absurdamente detallados.
- `languages-standards/javascript-mastery` — 33+ conceptos JavaScript core: primitivos, coerción de tipos, closures, event loop, patrones funcionales, prototipos y ES6+ moderno.
- `languages-standards/javascript-testing-patterns` — Guía de testing JS/TS de espectro completo: unit (Vitest/Jest), integración, componentes (Testing Library), E2E (Playwright), mocking con MSW, TDD y CI/CD.
- `languages-standards/modern-javascript-patterns` — Recetas de refactoring ES6+: migración async, pipelines funcionales, inmutabilidad, guard clauses, memoización, debounce/throttle e inicialización lazy.

### Modificado
- `languages-standards/testing-patterns` — Migrado completamente de Jest a mocking y assertions de **Vitest**.
- `frontend-ui/react-ui-patterns` — Actualizado para ser completamente autocontenido con ejemplos inline de estados loading/error/button en lugar de links a archivos separados.
- `tools-automation/documentation-expert` — Consolidado con `doc-writer` para cubrir bases de conocimiento de proyectos (directorio `.knowledge/`).

- Actualizados todos los playbooks a nivel de carpeta (archivos `README.md`) y el `README.md` raíz.
- `strategy-architecture/senior-architect` — **Actualizado** de stub mínimo a template completo de la comunidad: stack tecnológico expandido (Flutter, Kotlin, Terraform, AWS/GCP/Azure), framework de decisión ADR, checklist de escalabilidad y documentación de scripts enriquecida.

### Eliminado / Deprecado
- `backend-infra/backend-expert` — Consolidado en `nodejs-best-practices` y `database-design`.
- `strategy-architecture/planning-expert` — Deprecado en favor del modo de planificación nativo de Antigravity (`task.md` / `implementation_plan.md`).
- `product-building/writing-plans` — Deprecado/eliminado en favor de `plan-writing`.
- Eliminadas skills temporales/legacy/test: `add-about-page`, `add-health-endpoint`, `react-exam-copilot` y `react-frontend-patterns`.

---

## [1.2.0] - 2026-02-24

### Agregado

- Nueva categoría **`product-building`** — skills orientadas al ciclo completo de vida de un producto usando plataformas low-code/no-code + AI
- `lovable-saas-builder` skill — Workflow completo para construir SaaS B2B con Lovable Cloud + Supabase
  - Prompts estructurados para Design System, Auth, CRUD, Edge Functions e integraciones de pago
  - Patrones de Edge Functions reutilizables (OAuth, webhooks, AI, pagos)
  - Guía de deployment y go-live checklist
  - Basado en patrones extraídos del proyecto SoporteML

### Modificado

- `README.md`: agregada sección "Product Building Playbook" y entrada en el Capability Map

---

## [1.1.0] - 2026-02-06

### Agregado

- `react-exam-copilot` skill — Asistente para exámenes y desafíos de código React senior
  - Modo entrenamiento con soluciones completas y explicaciones
  - Modo examen con hints guiados (sin respuestas directas)
  - Checklists: accesibilidad, rendimiento, code review
  - Patrones: custom hooks, compound components, error boundaries, data fetching
  - Templates: componente, custom hook, setup de test, error boundary

### Modificado

- Actualizado `README.md` para incluir `react-exam-copilot` en la sección Frontend & UI/UX
- Actualizado `frontend-ui/README.md` con la skill en Fase 3 y tabla de Skill Index

---

## [1.0.0] - 2026-01-29

### Agregado

- Release inicial del Antigravity Developer Stack
- **IA & Agentes Autónomos**: autonomous-agent-expert, agent-tool-builder, llm-app-patterns, mcp-builder, prompt-mastery, rag-expert, chatgpt-project-architect, meta-skill-antigravity
- **Strategy & Architecture**: senior-architect, planning-expert, brainstorming, pricing-strategy, marketing-ideas, kaizen, app-builder
- **Backend & Infraestructura**: backend-expert, nestjs-expert, api-patterns, database-design, postgres-best-practices, docker-expert, mercadolibre-api
- **Frontend & UI/UX**: frontend-dev-guidelines, react-frontend-patterns, react-ui-patterns, react-migration-16-to-19, redux-migration-rtk-zustand, nextjs-best-practices, tailwind-patterns, ui-ux-pro-max
- **Tools & Automation**: browser-automation-expert, n8n-workflow-builder, pdf-official
- **Languages & Standards**: typescript-expert, testing-patterns
- Engineering Playbooks por dominio
