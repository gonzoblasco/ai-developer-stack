---
name: docs-sync
description: Skill to synchronize documentation when closing an epic/feature. Activated with "/docs-sync", "sync docs", "update docs", or as a step in epic closure.
risk: unknown
source: community
date_added: "2026-06-26"
---

# Docs Sync (Generic Template)

Detect which documentation has become out of sync with the changes in the current epic/feature and update it without asking for confirmation.

## When to use it

- **Mandatory** when closing each epic or major feature.
- Usually performed after final audits (security, linting) and before the final closure commit.
- Do not use for individual small PRs unless they significantly impact core documentation — the batch context of an epic is where this skill shines.

## Process

### 1. Diff Collection

List all files touched in the epic/feature:

```bash
git diff main...HEAD --name-only
```

### 2. Mapping & Discovery (Self-Referential)

**If this is the first time running in this repo or the mapping table below contains placeholders:**
1.  Scan the repository structure (e.g., `ls -R` or check `.knowledge/` folder).
2.  Identify the core modules and their corresponding documentation files.
3.  **Update this SKILL.md file** to replace the generic placeholders in the table below with the actual project mappings. This ensures future runs are faster and more accurate.

| Touched Files/Patterns                  | Potential Out-of-Sync Docs                                                         |
| ----------------------------------------| ----------------------------------------------------------------------------------|
| `app/vender/**`                          | `CLAUDE.md` (estructura), `ESTADO_PROYECTO_v0.15.0.md` (Next Steps)              |
| `app/admin/**`                           | `CLAUDE.md` (estructura), `ESTADO_PROYECTO_v0.15.0.md`                           |
| `app/api/**`                             | `ESTADO_PROYECTO_v0.15.0.md` (API Endpoints section), `CLAUDE.md`                |
| `prisma/schema.prisma`                   | `ESTADO_PROYECTO_v0.15.0.md` (Database Schema), `docs/ENTIDADES.md`              |
| `middleware.ts`                          | `ESTADO_PROYECTO_v0.15.0.md` (Protected Routes), `CLAUDE.md` (reglas)            |
| `package.json`                           | `ESTADO_PROYECTO_v0.15.0.md` (Architecture stack), `docs/CONVENCIONES.md`        |
| `.knowledge/AGENT_TASKS.md`              | `ESTADO_PROYECTO_v0.15.0.md` (Summary table status)                              |
| `CLAUDE.md`                              | Verificar que decisiones de arquitectura y estructura sean correctas              |
| `docs/ARCHITECTURE.md`                   | Al agregar nuevas capas (Redis, CDN, APM) en Fases 18-19                         |
| `components/**`                          | `ESTADO_PROYECTO_v0.15.0.md` (component count), `docs/CONVENCIONES.md`           |
| `Any file in the epic/fase`              | `.knowledge/AGENT_TASKS.md` — marcar tareas como [x] al completar               |

### 3. Read and Contrast

For each candidate document:
1. Read the **entire** current document.
2. Read the **diff** of the related files.
3. Determine if there's anything in the doc that is no longer true, or something in the code that the doc should mention but doesn't.

### 4. Verdict per Document

For each candidate doc, issue one of these verdicts:

- **SYNC** — The doc is out of sync; update it now.
- **OK** — The doc correctly reflects the current state of the code.

### 5. Immediate Action

- If the verdict is **SYNC**: Edit the document directly without presenting a plan or asking for permission.
- If the verdict is **OK**: Do nothing for that document.

## Rules

- **Self-Configuration**: If the mapping table is empty or generic (`REPLACE_ME`), the agent MUST populate it by analyzing the repository structure before proceeding with the sync.
- **Direct Action**: Do not present plans or ask for approval — the verdict *is* the action.
- **Surgical Edits**: Do not rewrite sections that haven't changed. Edit only the out-of-sync parts.
- **Creation**: If a document doesn't exist but should (e.g., a new core module was added), create it.
- **Contradictions**: If code contradicts a critical rule in `CLAUDE.md`, report it explicitly before proceeding.

## Final Output

```markdown
## Docs Sync — [Epic/Feature Name]

### Analyzed Docs
- `.knowledge/feature-a.md` → OK
- `.knowledge/schema.md` → SYNC ✏️ (updated: "users" table — new field `is_active`)
- `.knowledge/decisions/005-caching.md` → SYNC ✏️ (updated: TTL changed from 60s to 300s)

### Missing Documentation Gaps
- `src/experimental/new-tool.ts` — no doc covers this module (consider creating `.knowledge/experimental-tools.md`)

### Global Verdict
DOCS UP TO DATE / GAPS IDENTIFIED
```

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
