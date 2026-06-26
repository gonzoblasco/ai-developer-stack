---
name: commit
description: Formatear y crear un commit siguiendo Conventional Commits con las convenciones de este proyecto. Habilita la orquestación híbrida en CLI e IDE.
risk: safe
source: self
date_added: "2026-06-26"
---

# Skill: Commit (Conventional Commits & Estandarización de Historial)

## Propósito

Garantizar que cada confirmación en el historial de Git cumpla estrictamente con la especificación de **Conventional Commits** y las convenciones del proyecto. Esto permite la legibilidad humana, auditorías forenses limpias y la automatización futura de notas de lanzamiento (CHANGELOG y semantic versioning).

Usar este skill siempre antes de hacer push — nunca commitear con mensajes improvisados.

---

## Precondiciones

- Estar en una feature branch (nunca commitear directo a `main` o a la rama del epic)
- Los cambios que se quieren incluir deben estar listos para staging

## Invocación

```text
/commit
/commit "descripción breve de los cambios"
```

---

## Reglas de Formato General

```text
<tipo>(<scope opcional>): <descripción corta en minúsculas y modo imperativo>

[Cuerpo opcional: Qué cambió y por qué, nunca CÓMO se hizo]

[Footer opcional: BREAKING CHANGE o referencias a Issues/Tasks o Co-authorship]
```

### Restricciones Críticas

1. **Longitud:** La primera línea (header) jamás debe superar los **72 caracteres**.
2. **Caso:** La descripción corta comienza estrictamente en **minúscula** y no lleva punto final.
3. **Modo Imperativo:** Tiempo presente imperativo: "add feature" no "added feature" ni "adds feature".
4. **Contenido del Cuerpo:** Se explica el contexto de negocio o la decisión de ingeniería (el "por qué"). El código ya muestra el _cómo_.

---

## Tipología Permitida

| Tipo | Criterio de Uso |
|---|---|
| `feat` | Nueva funcionalidad directa para el usuario o sistema. |
| `fix` | Corrección de un bug o comportamiento anómalo. |
| `refactor` | Modificación de código que no añade features ni corrige bugs (limpieza). |
| `test` | Adición, modificación o corrección de pruebas unitarias/integración. |
| `docs` | Cambios exclusivos en documentación técnica, Markdown o comentarios. |
| `chore` | Tareas de mantenimiento: actualización de dependencias, scripts, configs. |
| `perf` | Optimización de código enfocada puramente en rendimiento/memoria. |
| `ci` | Cambios en pipelines de integración continua o flujos de despliegue. |

Si el commit mezcla tipos, dividir en dos commits separados. Si no se puede dividir razonablemente, usar el tipo dominante.

---

## Determinar el Scope

El scope indica qué área del sistema cambió. Debe ser consistente entre commits del mismo epic.

Convención: scopes son capas del sistema (auth, db, api) o dominios de negocio (catalog, payments, admin).

Ejemplos:
- Proyecto web: auth, catalog, cart, payments, admin, db, notifications
- App mobile: auth, feed, profile, messaging, db
- Backend/API: auth, users, orders, payments, db, integrations
- Librería: core, utils, types, hooks, components

Si el cambio es transversal a varios scopes, se puede omitir el scope (dejar solo el tipo).

---

## Flujo de Orquestación Híbrida

### 1. Preparación y Revisión (CLI)

Antes de commitear, inspeccionar el estado actual del repositorio:
```bash
git status
git diff --staged   # si ya hay cosas staged
git diff            # si todavía no hay nada staged
```

Si no hay nada staged, hacer `git add` de los archivos relevantes primero. No usar `git add .` a ciegas.

### 2. Creación del Commit

#### En Claude Code (Terminal)
El agente automatiza el commit tras pasar el Build Check ejecutando:
1. `git add` de los archivos seleccionados.
2. Generación del mensaje bajo este estándar.
3. Inserción opcional del footer de autoría si aplica:
   `Co-Authored-By: Antigravity AI <noreply@gemini.com>`

```bash
git commit -m "feat(scope): descripción breve

Explicación opcional del por qué. El diff ya muestra el qué."
```

#### En Google Antigravity 2.0 (Editor/IDE)
El agente integrado lee este archivo y procesa el área de *Staged Changes* de la UI:
1. Analiza el diff actual en el panel lateral.
2. Escribe el mensaje formateado directamente en el cuadro de texto de la interfaz de Git.
3. Le permite al usuario hacer clic en el botón nativo de "Commit" con el texto ya validado.

---

## Validación

El commit es correcto si:
- `git log --oneline -1` muestra el mensaje con el formato correcto.
- `git show --stat` muestra exactamente los archivos esperados (nada extra).
- Cumple Conventional Commits: `<tipo>(<scope>): descripción`.

---

## Ejemplos de Mensajes

### Buenos Ejemplos
```text
feat(auth): add email verification on signup

Email verification was missing — users could sign up with invalid emails.
Added resend logic with 60s cooldown.
```

```text
fix(api): return 404 when resource not found instead of empty array
```

```text
refactor(core): extract validation logic to separate module
```

### Malos Ejemplos
```text
fix: stuff                          ← no describe qué se arregló
WIP                                 ← no es un commit finalizado
feat: Add new feature.              ← mayúscula inicial + punto final
update files                        ← sin tipo, sin scope, sin descripción útil
BREAKING CHANGE: everything        ← breaking changes van en body, no en subject
```

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
