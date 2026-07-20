# 🧪 Workflow: Calidad y Testing

## Objetivo

Establecer una cultura de calidad desde el primer commit: TDD, tests unitarios, de integración, E2E y CI/CD que los ejecute.

## Skills involucradas

| Fase | Skill | Propósito |
|------|-------|-----------|
| 1. Estrategia | `testing-patterns` | Unit testing con Vitest, mock factories |
| 2. Full spectrum | `javascript-testing-patterns` | Unit, integración, E2E, MSW, TDD |
| 3. E2E | `e2e-testing-patterns` | Playwright, browser testing |
| 4. PR Review | `pr-review` | Linter cognitivo pre-merge |
| 5. CI/CD | `github-actions-templates` | Pipelines de testing automático |
| 6. Code Review | `vibers-code-review` | Triggers de revisión humana |
| 7. Análisis | `analyze-project` | Diagnóstico de patrones de rework |

## Flujo

```
TDD → Unit → Integration → E2E → CI/CD → Review
```

## Outputs

- Suite de tests (unit, integration, E2E)
- Pipeline de CI/CD verde
- PRs revisados automática y humanamente
- Métricas de calidad
