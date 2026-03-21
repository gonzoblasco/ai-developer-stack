---
name: meta-skill-antigravity
description: Use cuando necesites crear, editar o validar skills. Trigger: "crear skill", "nueva funcionalidad", "reglas de diseño".
---

# Meta Skill Creator - SUPER CREADOR Edition

## Overview

**Crear skills es Test-Driven Development aplicado a la inteligencia artificial.** Este skill fusiona la disciplina TDD de Antigravity con principios de eficiencia de prompts avanzados.

> [!IMPORTANT]
> **El contexto es un bien público.** No lo malgastes. Antigravity ya es inteligente; solo dale el contexto que *no* tiene (conocimiento de dominio, workflows específicos, guardrails).

---

## Core Principles

### 1. Progressive Disclosure (3 Niveles)
1. **Metadata**: Trigger en la `description` (~100 tokens).
2. **SKILL.md**: El core del workflow (< 500 líneas).
3. **Bundled Resources**: Detalles en `references/`, `scripts/` o `templates/` (On demand).

### 2. Degrees of Freedom
Ajusta la especificidad según la fragilidad de la tarea:
- **Alta Libertad** (Instrucciones de texto): Múltiples caminos válidos.
- **Media Libertad** (Pseudo-código/Scripts con parámetros): Patrón preferido con variaciones.
- **Baja Libertad** (Scripts específicos, cero parámetros): Tareas frágiles y críticas.

### 3. The Iron Law (TDD)
**NO SKILL WITHOUT FAILING TEST FIRST.**
Si no puedes probar que el agente falla sin el skill (Rationalization), tal vez no necesitas el skill.

---

## Skill Creation Process (6 Pasos)

### 1. Entender el Problema (Concrete Examples)
Gather examples. ¿Qué funcionalidad falta? ¿Cuándo falla el agente?

### 2. Planificar Recursos Reutilizables
¿Qué irá en `scripts/` (automatización), `templates/` (boilerplate) o `references/` (docs)?

### 3. Inicializar (init_skill.py)
```bash
python scripts/init_skill.py <nombre-skill> --type [domain|guardrail|reference]
```

### 4. RED Phase: Baseline Test
Ejecuta el escenario de fallo (Pressure Scenario) SIN el skill activo. Documenta las **excusas** del agente.

### 5. GREEN Phase: Implementar & Contra-medidas
Edita el `SKILL.md`. Ataca específicamente las racionalizaciones del baseline.
- **Bulletproofing**: Usa tablas de "Excusa vs Realidad".
- **Imperativo**: "Borrar significa borrar".

### 6. REFACTOR & Verify
Ejecuta con el skill. ¿Pasó? ¿Nuevas excusas? Itera.

---

## Estructura de una Skill

```
skill-name/
├── SKILL.md              # Core (requerido, < 500 líneas)
├── references/           # Documentación extendida (Nivel 3)
├── scripts/              # Código ejecutable
├── templates/            # Plantillas reutilizables
└── examples/             # Ejemplos prácticos / Casos TDD
```

---

## Scripts y Herramientas

```bash
# Inicializar con estructura estándar
python scripts/init_skill.py <nombre>

# Validar reglas (Lines < 500, Frontmatter, Degrees of Freedom)
python scripts/validate_skill.py <nombre> --validate

# Guías de Testing TDD
python scripts/validate_skill.py <nombre> --baseline
python scripts/validate_skill.py <nombre> --test
```

---

## Referencias Avanzadas

- [Degrees of Freedom](references/degrees-of-freedom.md) - Cómo guiar sin asfixiar.
- [Context Efficiency](references/context-efficiency.md) - Maximización del context window.
- [Testing Methodology TDD](references/testing-methodology.md) - Red/Green/Refactor en docs.
- [CSO Optimization](references/cso-optimization.md) - Optimizando el disparador (description).
