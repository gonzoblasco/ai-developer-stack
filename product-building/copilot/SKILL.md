---
name: copilot
description: Orquestador universal de workflow. Gobierna el ciclo de vida de las tareas y valida el pre-flight check.
risk: none
source: self
date_added: "2026-06-26"
---

# Skill: Copilot (Orquestador Universal de Workflow)

## Propósito

Actuar como la autoridad de flujo de trabajo definitiva del repositorio. Este skill gobierna el ciclo de vida de cada tarea e impide la ejecución desordenada o el avance ciego sin validaciones estructurales. Garantiza consistencia total tanto en la terminal (Claude Code) como en el entorno visual del IDE (Google Antigravity).

## Filosofía de Operación

Un copiloto lee los instrumentos antes de cada maniobra, advierte antes de que ocurra un error (no después), detiene la marcha hasta recibir confirmación explícita del piloto y reporta cada estado de forma transparente.

---

## El Checklist Pre-Flight (Obligatorio antes de codear)

Antes de modificar o crear cualquier archivo, el agente (sea en Claude Code o Antigravity) debe validar este estado y comunicarlo al usuario:

```text
PRE-FLIGHT E[N] · [Nombre del Epic]
─────────────────────────────────────────────
[ ] CLAUDE.md / Instrucciones Base leídas.
[ ] .knowledge/AGENT_TASKS.md revisado para el Epic actual.
[ ] Guía de estilos y arquitectura asimilada.
[ ] Mockups o contratos de API localizados.
[ ] Rama del Epic/Task creada correctamente.
[ ] Estado de branch 'main' limpio y actualizado.
[ ] Dependencias y prerrequisitos del Epic confirmed.

PRIMER TASK SELECCIONADO: T0X · [Nombre]
ESPERANDO CONFIRMACIÓN DEL DESARROLLADOR PARA COMENZAR.
```

---

## El Ciclo de Vida del Task (Los 5 Gates Híbridos)

### Gate 0: Branching Aislado

- **Acción:** Crear o moverse a una rama específica para la tarea actual.
- **Formato:** `e[Número-Epic]/t[Número-Task]-[descripción-corta]` (ej. `e4/t10-ai-copilot-drawer`).
- **Nota Antigravity:** Si se trabaja desde la UI, el agente debe solicitar la creación de la rama o advertir si se está editando directo en `main` de manera no planificada.

### Gate 1: Implementación Atómica y Acotada

- **Acción:** Escribir código única y exclusivamente para cumplir el alcance de la tarea actual (`T0X`).
- **Restricción:** Queda terminantemente prohibido el _feature creep_ (resolver problemas de la tarea siguiente o refactorizar código fuera de alcance).

### Gate 2: Build Check Estricto (Caja de Seguridad)

- **Acción:** Ejecutar el comando de producción real (ej. `npm run build`, `cargo build`, etc.). No basta con el modo desarrollo (`dev`).
- **Bloqueo:** Si el build falla por tipado, referencias rotas o errores de compilación, el agente debe detenerse inmediatamente, corregir el error en caliente y re-correr el build. **No se avanza al Gate 3 sin build exitoso.**

### Gate 3: Registro en CHANGELOG

- **Acción:** Documentar el cambio inmediatamente en el archivo `CHANGELOG.md` del repositorio bajo la sección temporal `[Unreleased]`.
- **Formato:** Un bullet point preciso por cada archivo modificado de forma sustancial.

### Gate 4: Commit Formateado y PR-Review

- **Acción:** Delegar el mensaje de confirmación al sub-skill `@commit`.
- **Acción 2:** Ejecutar una auditoría de código local sobre el diff generado (`git diff main...HEAD`).
- **Bloqueo:** Si el review arroja un veredicto `REQUEST CHANGES` (rojos/bloqueantes), se debe corregir el código antes de enviar o mergear el PR.

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
