# Pull Requests (PR)

Habilidad y flujo automatizado para la creación de Pull Requests (PRs) con descripción estructurada, ejecución de revisiones locales y fusión (merge) de ramas tras su aprobación en Git.

## Resumen

Esta habilidad guía el cierre formal de cada tarea de desarrollo. Establece las precondiciones de compilación locales, automatiza la creación de PRs contra la API de GitHub, provee plantillas de descripción técnica estructuradas y prescribe el método de fusión estándar para conservar el grafo histórico sin pérdida de trazabilidad.

## Inicio Rápido

Para iniciar el flujo de creación de un Pull Request:

1. **Precondición**: Asegúrate de que no existan errores de compilación y que la rama esté limpia y empujada al repositorio remoto:
   ```bash
   npm run build
   git status # Debe estar limpio
   git push -u origin $(git branch --show-current)
   ```
2. **Generar el PR**: Lanza el comando `/pr` para invocar el script automatizado. Si lo creas manualmente, sigue el formato de título Conventional Commits: `<tipo>(<scope>): descripción`.

## Qué Incluye

- **Plantilla de Cuerpo de PR (PR Body Template)**: Secciones obligatorias para describir el impacto del cambio, archivos técnicos principales modificados, pasos de testing manual y lista de control de higiene (sin console.logs, sin secrets).
- **Proceso de Automatización API**: Llamadas `curl` estructuradas para interactuar con la API de GitHub usando `GITHUB_TOKEN` para la creación y posterior fusión del PR.
- **Política de Fusión**: Preferir siempre el método `merge` ordinario en lugar de `squash` para conservar la historia individual de cada commit de la tarea.
- **Limpieza Post-Merge**: Regreso ordenado a la rama `main` y actualización (`git pull`), manteniendo la rama local como memoria de desarrollo.

## Conceptos Clave

- **Unificación de Conventional Commits**: Los tipos (`feat`, `fix`, `refactor`, `chore`) y alcances (scopes) del título del PR deben coincidir exactamente con las convenciones definidas para los commits individuales del proyecto.
- **Evitar PRs Multipropósito**: Un PR debe cubrir estrictamente una sola tarea. Evita mezclar refactorizaciones extensas o cambios en módulos no relacionados en el mismo Pull Request.

## Estructura de la Habilidad

```
pr/
├── SKILL.md                 # Flujo, comandos API y plantilla de PR
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [commit](../../languages-standards/commit/README.md) - Formateo de mensajes unitarios en Git.
- [copilot](../copilot/README.md) - Validación de puertas del ciclo de vida (Gates).
- [close-epic](../close-epic/README.md) - Consolidación final y etiquetado de Epics.
