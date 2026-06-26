---
name: close-epic
description: Ritual de consolidación, versionado y cierre de bloques de desarrollo estratégico (Epics) en Git.
risk: safe
source: self
date_added: "2026-06-26"
---

# Skill: Close Epic (Ritual de Consolidación y Versionado)

## Propósito

Gobernar la finalización formal de un bloque de desarrollo estratégico (Epic). Coordina la auditoría de seguridad macro, el congelamiento de versiones mediante etiquetas (Tags) de Git y el resguardo del conocimiento institucional en el repositorio.

---

## Los 7 Pasos del Ritual (Orden Secuencial Inalterable)

### Paso 1: Auditoría de Seguridad Macro (Security Audit)

- **Acción:** Invocar obligatoriamente el sub-skill `@security-audit`. Se escanean todos los nuevos endpoints y cambios del Epic de forma profunda.
- **Bloqueo:** Si hay fallas de aislamiento, fugas potenciales de datos o falta de tokens de seguridad, el cierre se cancela inmediatamente.

### Paso 2: Consolidación Definitiva del CHANGELOG

- **Acción:** Mover todos los bullet points acumulados en `[Unreleased]` hacia una nueva versión semver oficial con la fecha actual del sistema.
- **Formato:** `## [MAJOR.MINOR.PATCH] — YYYY-MM-DD · E[N] · [Nombre Epic]`

### Paso 3: Actualización de Historial en AGENT_TASKS.md

- **Acción:** Marcar el Epic completo con el emoji `✅`. Registrar la fecha de cierre, el hash o ID del merge commit, los tags generados y un bloque de **"Lecciones Aprendidas"**.

### Paso 4: Commit Exclusivo de Documentación

- **Acción:** Realizar un commit que contenga _únicamente_ las modificaciones a la documentación de control (`CHANGELOG.md` y `AGENT_TASKS.md`).
- **Mensaje:** `docs: cerrar E[N] formalmente en logs de control`

### Paso 5: Integración Limpia mediante Merge `--no-ff`

- **Acción:** Cambiar a la rama principal (`main`), traer los cambios remotos y fusionar la rama del epic forzando un commit de merge.
- **Comandos:**
  ```bash
  git checkout main
  git pull origin main
  git merge --no-ff epic/e[N]-[nombre] -m "merge: fusionar epic E[N] - [Nombre]"
  git push origin main
  ```

*Por qué:* El flag `--no-ff` (no-fast-forward) preserva la estructura de la rama en el grafo histórico de Git, aislando visualmente el ciclo de vida del Epic.

### Paso 6: Generación de Tag Permanente (Punto de Restauración)

* **Acción:** Crear una etiqueta anotada en Git para marcar el entregable estable del proyecto.
* **Comandos:**
```bash
git tag -a E[N]-complete -m "Release estable del Epic [N]"
git push origin --tags
```

### Paso 7: Reporte Ejecutivo Final

- **Acción:** Presentar un resumen en pantalla indicando: total de tareas cerradas, endpoints securizados, versión asignada y el recordatorio explícito al desarrollador humano de replicar estas notas si maneja herramientas de planificación externas (como Claude.ai Projects).

---

## Regla de Oro de Infraestructura

⚠️ **PROHIBIDO EL AUTO-DELETE DE BRANCHES:** Las ramas de los Epics y Tasks locales y remotas no deben eliminarse de forma destructiva post-merge. Se conservan intencionalmente como parte de la memoria técnica y pedagógica del repositorio.

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
