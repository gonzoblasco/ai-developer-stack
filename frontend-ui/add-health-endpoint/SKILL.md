---
name: add-health-endpoint
description: Agrega un endpoint GET /health minimalista en proyectos Next.js (App o Pages router) que retorna JSON {"ok":true}, e incluye comandos de verificación en el README.
---

# Skill: Add Health Endpoint (Next.js)

> Usa esta skill para crear rápidamente un punto de chequeo de salud (health check) en proyectos Next.js, esencial para despliegues, monitoreo y CI/CD.

## 🗺️ Mapa de Recursos

Lee estos archivos según el enrutador y lenguaje detectado:

| Recurso                   | Ruta                          | Cuándo usar                          |
| ------------------------- | ----------------------------- | ------------------------------------ |
| Plantilla App Router TS   | `templates/app-router.ts`     | Proyecto usa `app/` y TypeScript     |
| Plantilla App Router JS   | `templates/app-router.js`     | Proyecto usa `app/` y JavaScript     |
| Plantilla Pages Router TS | `templates/pages-router.ts`   | Proyecto usa `pages/` y TypeScript   |
| Plantilla Pages Router JS | `templates/pages-router.js`   | Proyecto usa `pages/` y JavaScript   |
| Snippet README MD         | `templates/readme-snippet.md` | Al actualizar o crear el `README.md` |

## 🎯 Cuándo Usar Esta Skill

**SÍ:**

- El usuario quiere agregar un endpoint `/health` o un health check a un proyecto Next.js.
- Se necesita documentar localmente (en README) cómo verificar el endpoint.

**NO:**

- El proyecto no es Next.js (ej. es un backend de Node puro O Vite SPA sin middleware/API).

## ⚙️ Detección de Entorno (Automática)

Antes de empezar, determina:

1. **Router mode**:
   - Si existe la carpeta `app/` → Usa **App Router**.
   - Solamente si NO existe `app/` y existe `pages/` → Usa **Pages Router**.
   - Si no existe ninguno de los dos → Detente y pide clarificación.
2. **Lenguaje**:
   - Si existe `tsconfig.json` → Usa **TypeScript** (`.ts`).
   - Si no existe → Usa **JavaScript** (`.js`).

## ⚡ Flujo de Trabajo (Strict Workflow)

### Paso 1. Preparación y Plan

Analiza el entorno y escribe un plan de implementación detallando:

- El modo de enrutador detectado y lenguaje.
- Los archivos exactos que se van a crear (ej: `app/health/route.ts`).
- Tareas concretas (Checklist).

### Paso 2. Implementación del Endpoint

Copia el contenido de la plantilla correspondiente desde `templates/` hacia el archivo destino:

- **App Router**: Crea/modifica `app/health/route.(ts|js)` o `app/api/health/route.(ts|js)` (dependiendo de la convención existente, prefiere `app/health/route.(ts|js)` a menos que exista una convención fuerte de poner endpoints bajo `app/api`).
- **Pages Router**: Crea/modifica `pages/api/health.(ts|js)`.

### Paso 3. Actualización de README

Abre `README.md` (créalo si no existe) e inserta el snippet que se encuentra en `templates/readme-snippet.md` adaptando el puerto `<port>` si detectas que es distinto de 3000.

### Paso 4. Verificación

Entrega al usuario los comandos exactos para ejecutar:

- `npm run dev` (o el equivalente).
- `curl -i http://localhost:<port>/health` (o `/api/health` en Pages router o si se usó la carpeta `api/`).

## ✅ Criterios de Aceptación

- El request GET al endpoint devuelve **HTTP 200**.
- El header de la respuesta contiene `content-type: application/json`.
- El body de la respuesta es exactamente `{"ok":true}` (o con espacios válidos).

## ⚠️ Reglas Críticas

1. **No inventes código**: Copia el código exacto de la carpeta `templates/`.
2. **No finjas ejecución**: Al entregar instrucciones de validación con `curl`, entrégaselas al usuario para que él las ejecute, NO afirmes que ya las corriste.
3. **Mantén el foco**: No modifiques archivos no relacionados al endpoint y al README.
