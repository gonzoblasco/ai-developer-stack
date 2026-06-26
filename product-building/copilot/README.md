# Copilot (Orquestador Universal de Workflow)

Habilidad de gobernanza de ciclo de vida del desarrollo. Actúa como la autoridad de flujo de trabajo definitiva del repositorio para asegurar una ejecución estructurada y ordenada de tareas.

## Resumen

Esta habilidad define las reglas del rol de orquestador de desarrollo. Administra el flujo de trabajo impidiendo el avance a ciegas mediante la verificación de listas de comprobación previas al vuelo (Pre-Flight Checklists) y la validación de 5 puertas de control (Gates) del ciclo de vida de cada tarea antes de ser integradas.

## Inicio Rápido

Antes de escribir código o modificar el repositorio, presenta la plantilla de verificación previa:

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

## Qué Incluye

### Los 5 Gates del Ciclo de Vida del Task
- **Gate 0: Branching Aislado**: Creación de ramas específicas con nomenclatura estricta (`e[Número-Epic]/t[Número-Task]-[descripción]`).
- **Gate 1: Implementación Atómica**: Foco exclusivo en la tarea en curso, prohibiendo el *feature creep*.
- **Gate 2: Build Check Estricto**: Validación de compilación en producción (ej. `npm run build` o `cargo build`).
- **Gate 3: Registro en CHANGELOG**: Documentación inmediata de cambios en la sección `[Unreleased]`.
- **Gate 4: Commit y PR-Review**: Formateo de confirmaciones delegadas e inspección del diff generado contra `main`.

## Conceptos Clave

- **Comportamiento Preventivo**: Advertir fallos antes de ejecutar cambios en lugar de recuperarse después de que el código falle.
- **Detención por Falla de Compilación**: No pasar a la documentación o commits si la compilación del proyecto presenta errores.

## Estructura de la Habilidad

```
copilot/
├── SKILL.md                 # Guía y checklist del orquestador de flujos
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [new-task](../new-task/README.md) - Inicialización y andamiaje de tareas de desarrollo.
- [pr](../pr/README.md) - Preparación de Pull Requests de código.
- [commit](../../languages-standards/commit/README.md) - Formateo y estandarización de mensajes de Git.
