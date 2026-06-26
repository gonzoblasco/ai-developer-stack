# New Task

Guía y comandos estructurados para inicializar de forma ordenada nuevas tareas (Tasks) pertenecientes al Epic activo en el repositorio.

## Resumen

Esta habilidad impone un orden estricto de desarrollo: primero leer y comprender el contexto, luego planificar y, por último, implementar. Evita el retrabajo derivado de asunciones apresuradas obligando a verificar los criterios de aceptación, crear ramas aisladas en Git, verificar el entorno local y compilar la aplicación antes de marcar la tarea como completada.

## Inicio Rápido

Para inicializar la tarea `T02` del Epic `E1`:

1. **Revisar criterios de aceptación**: Abre `AGENT_TASKS.md` y comprueba que los requisitos para `E1-T02` sean claros y cuantificables. Si son ambiguos, solicita aclaraciones.
2. **Crear la rama aislada**:
   ```bash
   git checkout main && git pull origin main
   git checkout -b task/E1-T02-auth-flow
   ```
3. **Validar entorno**: Inicia el servidor de desarrollo local y comprueba que no existan errores previos antes de escribir código:
   ```bash
   npm run dev
   ```

## Qué Incluye

- **Lectura de Precondiciones**: Instrucciones para verificar `CLAUDE.md`, variables de entorno y guías de arquitectura antes de codificar.
- **Flujo de Tareas en 8 Pasos**:
  1. Lectura de descripción y criterios de aceptación.
  2. Asimilación de conocimientos específicos del proyecto (`.knowledge/`).
  3. Creación de la rama descriptiva en Git.
  4. Testeo previo del entorno de desarrollo.
  5. Codificación atómica y estructurada.
  6. Control de calidad y build final (`npm run build`).
  7. Creación del Pull Request.
  8. Actualización de estado y cierre en `AGENT_TASKS.md`.
- **Análisis de Modos de Falla Comunes**: Explicación de los errores habituales como programar sin leer restricciones de diseño o acumular demasiados cambios en un solo commit.

## Conceptos Clave

- **Criterios de Aceptación Inequívocos**: No programar si el criterio de la tarea es vago (ej: "que funcione"). Los criterios deben definir estados específicos (ej: "validar email antes de enviar", "mensaje de éxito visible por 2 segundos").
- **Código Delgado en Handlers**: Delegar la lógica pesada a librerías y utilidades en `/lib/`, manteniendo los controladores e interfaces de componentes limpios y desacoplados.

## Estructura de la Habilidad

```
new-task/
├── SKILL.md                 # Guía y flujo del ciclo de vida de una tarea
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [copilot](../copilot/README.md) - Orquestación general del flujo y validación del Pre-Flight Check.
- [pr](../pr/README.md) - Preparación e integración de Pull Requests.
- [commit](../../languages-standards/commit/README.md) - Formateo de commits unitarios.
