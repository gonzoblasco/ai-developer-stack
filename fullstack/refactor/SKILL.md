---
name: refactor
description: Refactoriza código existente para mejorar legibilidad, reducir duplicación y alinear con las convenciones del proyecto, sin cambiar comportamiento.
risk: unknown
source: community
date_added: "2026-06-26"
---

# Skill: refactor

## Qué hace

Refactoriza código existente para mejorar legibilidad, reducir duplicación y alinear con las convenciones del proyecto, sin cambiar comportamiento.

## Cuándo usarlo

- Después de un pr-review con observaciones de código
- Cuando hay duplicación evidente entre Server Actions o componentes
- Antes de extender una feature que tiene deuda técnica

## Proceso

1. Leer `.knowledge/conventions.md` para entender los patrones del proyecto
2. Identificar: duplicación, funciones largas, nombres poco claros, imports muertos
3. Refactorizar en commits atómicos — un cambio por commit
4. Nunca cambiar comportamiento observable — si algo puede cambiar, preguntar primero
5. Correr `tsc --noEmit` antes y después para confirmar que no hay regresiones de tipos

## Patterns a aplicar

- Extraer lógica repetida a helpers en `/lib/utils/`
- Dividir componentes > 150 líneas en sub-componentes
- Unificar manejo de errores en Server Actions
- Reemplazar `any` por tipos explícitos

## Output esperado

Commits atómicos con mensaje `refactor: <descripción concisa del cambio>`

## Warnings

- No refactorizar y agregar features en el mismo commit
- Si el refactor requiere cambios en tests, actualizarlos en el mismo commit
- No cambiar nombres de exports públicos sin revisar todos los imports primero
