---
name: new-task
description: Inicializar una nueva task del epic activo. Define flujo de lectura de contexto, precondiciones de branch, verificación de entorno y criterios de aceptación.
risk: unknown
source: community
date_added: "2026-06-26"
---

# new-task

## Propósito

Inicializar una nueva task del epic activo. El valor de este skill está en el orden:
primero leer, luego planificar, recién entonces implementar.

El error más costoso de un agente es empezar a escribir código antes de entender
las restricciones del sistema y los criterios de aceptación.

## Contexto a leer primero

- `AGENT_TASKS.md` — descripción completa de la task y sus criterios de aceptación
- `CLAUDE.md` — reglas críticas activas para este proyecto
- Los archivos de `.knowledge/` específicos indicados en la task

## Precondiciones

- Estar en `main` con pull reciente: `git checkout main && git pull origin main`
- El epic activo está marcado en `AGENT_TASKS.md`
- La task tiene criterios de aceptación definidos (si no los tiene, definirlos antes de empezar)

## Invocación

```
/new-task [epic]-[task]
```

Ejemplos:
```
/new-task E1-T02
/new-task E0-T05
```

---

## Pasos

**1. Leer la task en AGENT_TASKS.md**

Leer la descripción completa de la task: qué hace, por qué existe, y los criterios de aceptación.

Si los criterios de aceptación no están definidos o son ambiguos, **DETENER y pedir clarificación**
antes de crear la branch. Implementar sin criterios claros garantiza retrabajo.

Criterios bien definidos se ven así:
```
Acceptance criteria:
- [ ] `npm run dev` arranca sin errores
- [ ] El formulario valida email antes de enviar
- [ ] Los datos se persisten en Supabase
- [ ] El usuario ve mensaje de éxito después de 2 segundos
```

Criterios mal definidos:
```
Acceptance criteria:
- [ ] La feature funciona
```

**2. Leer el conocimiento relevante**

Leer los archivos de `.knowledge/` que el mapa de `CLAUDE.md` o la task indican.

No asumir que se recuerda el contenido de sesiones anteriores — leer siempre.

Archivos mínimos a leer para CUALQUIER task:
- `CLAUDE.md` — stack, reglas críticas, environment variables
- Cualquier `.knowledge/` file que la task mencione explícitamente

Archivos adicionales según el tipo de task:
- ¿Toca la base de datos? → leer `schema.md` o documento equivalente
- ¿Es UI? → leer `style-guide.md` o documento de diseño
- ¿Es integración? → leer docs de la integración externa

**3. Crear la branch**

```bash
git checkout -b task/E[N]-T[NN]-[nombre-corto]
```

Convención: `task/` + identificador de la task + nombre descriptivo corto (2-3 palabras, kebab-case).

Ejemplos:
```
task/E1-T01-auth-flow
task/E2-T03-data-loading
task/E3-T02-form-validation
```

**4. Verificar que el entorno de desarrollo funciona**

```bash
npm run dev
```

O equivalente para tu proyecto (`yarn dev`, `pnpm dev`, `go run`, etc.).

Si hay errores de arranque: resolverlos antes de empezar a escribir código nuevo.
Implementar sobre un entorno roto garantiza horas de debugging innecesario.

Verificar que:
- La app levanta sin errores
- Las herramientas de dev funcionan (hot reload, etc.)
- Las variables de `.env` están configuradas

**5. Implementar**

Con el contexto completo y el entorno funcionando, implementar la task.

Principios de implementación (según el stack):

*Para proyectos web/Node.js:*
- La lógica de negocio va en `lib/` — nunca en route handlers ni en componentes
- Los route handlers son delgados: extraer input → llamar lib/ → retornar respuesta
- Cada función en `lib/` maneja errores con prefijos tipados (ver error contract en `CLAUDE.md`)
- Commitear con `/commit` al terminar cada unidad coherente de trabajo — no acumular todo para un solo commit al final

*Para proyectos en general:*
- Seguir las convenciones definidas en `CLAUDE.md` y `.knowledge/conventions.md`
- No hardcodear credenciales, secrets, o datos de contacto
- Validar input del usuario antes de procesar

**6. Verificar calidad antes de continuar**

```bash
npm run build    # debe pasar sin errores ni warnings
npm run dev      # probar manualmente el flujo principal de la task
```

Si el build falla: resolver antes de avanzar. Un build roto que se acumula es exponencialmente
más difícil de debuggear que uno resuelto inmediatamente.

**7. Crear el PR**

```bash
/pr
```

El skill `/pr` maneja: verificar build, pushear, crear PR, correr review, mergear.

**8. Actualizar el estado en AGENT_TASKS.md**

Cambiar el estado de la task a ✅ (complete) cuando el PR esté mergeado.
Registrar el número del PR en el campo correspondiente.

---

## Validación

La task está correctamente inicializada si:
- Se leyeron los archivos de `.knowledge/` relevantes ANTES de escribir código
- La branch existe con el nombre correcto
- `npm run dev` arranca sin errores antes de empezar a implementar
- Los criterios de aceptación estaban claros antes de arrancar

Una task está **completa** cuando:
- El PR se mergeó
- TODOS los criterios de aceptación en AGENT_TASKS.md están marcados con ✅
- No hay bloqueantes pendientes de `/review`

## Modos de falla comunes

**Empezar a implementar sin leer `.knowledge/`.** El agente asume que recuerda las
restricciones del sistema de sesiones anteriores. No las recuerda. El resultado es código
que viola reglas críticas y que el pr-review va a bloquear.

**No verificar `npm run dev` antes de implementar.** Si el entorno ya estaba roto antes de
la task, es imposible saber si los errores nuevos son culpa de la tarea o preexistentes.
Siempre partir de un entorno limpio.

**Criterios de aceptación ambiguos.** Implementar sin saber exactamente qué significa
"hecho" garantiza retrabajo. Si los criterios dicen "la UI muestra los datos", eso es
ambiguo — ¿todos los datos? ¿con qué formato? ¿con manejo de estados vacíos? Aclarar
antes de implementar, no después.

**Acumular demasiado en un solo commit.** Commits grandes son difíciles de revisar y
difíciles de revertir. Commitear al terminar cada unidad coherente: un componente,
una función, una migración. No al final de la jornada.
