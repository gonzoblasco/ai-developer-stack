# Not-a-Vibe-Coder

Estrategia de planificación estructurada y persistencia de memoria para proyectos de software nuevos, transformando ideas abstractas en 8 documentos vivos de diseño y desarrollo.

## Resumen

Esta habilidad regula la fase de andamiaje y concepción de proyectos completamente nuevos (desde cero). Su propósito es evitar el desarrollo desestructurado (vibe-coding) creando un historial escrito que sirve como memoria de contexto para la IA. Define el flujo secuencial de generación de 8 archivos clave y establece reglas críticas sobre la primacía de las órdenes del usuario sobre los supuestos de la máquina.

> [!CAUTION]
> **CRÍTICO:** Utilizar esta habilidad ÚNICAMENTE al iniciar proyectos desde cero. Si el repositorio ya contiene archivos de código funcional, cancela su ejecución para evitar sobreescrituras accidentales.

## Inicio Rápido

Al recibir la idea inicial de un proyecto (ej: "quiero una app para reservas de restaurantes"):

1. **Fase 0 - Detección**: Asegúrate de que el codebase esté vacío.
2. **Fase 1 - PRD.md**: Formula preguntas puntuales al usuario sobre audiencias, características core y alcances, antes de escribir nada.
3. **Fase 2 - Generación secuencial**: Crea y valida los archivos uno a uno en el siguiente orden estricto:
   `PRD.md` → `TechSpec.md` → `AppFlow.md` → `Schema.md` → `ImplementationPlan.md` → `Rules.md` → `Tracker.md` → `Design.md`.

## Qué Incluye

### Los 8 Documentos del Proyecto
1. **`PRD.md`**: Requerimientos del producto, funcionalidades y alcance.
2. **`TechSpec.md`**: Arquitectura, stack tecnológico, APIs y bases de datos.
3. **`AppFlow.md`**: Flujos de navegación y experiencia del usuario.
4. **`Design.md`**: Estilos de UI/UX, paleta de colores y tipografía. *(Requiere consulta interactiva obligatoria sobre estética antes de crearse)*.
5. **`Schema.md`**: Modelos de datos, relaciones y tablas.
6. **`ImplementationPlan.md`**: Hoja de ruta técnica detallada paso a paso.
7. **`Tracker.md`**: Log dinámico de tareas completadas y pendientes.
8. **`Rules.md`**: Restricciones de código, guías de estilo y convenciones.

## Conceptos Clave

- **La voz del usuario es ley**: Si hay una contradicción entre lo que pide el usuario en chat y lo escrito en los archivos, prevalece el usuario. Los archivos deben actualizarse inmediatamente para reflejar la nueva decisión.
- **Sin asunciones estéticas**: Nunca decidas la paleta cromática o el estilo visual de `Design.md` por cuenta propia; ofrece siempre 2 o 3 opciones para que el usuario seleccione.
- **Tracker Dinámico**: Mantener `Tracker.md` actualizado en cada commit. No modificar el historial del tracker, solo marcar tareas completadas y agregar las nuevas.

## Estructura de la Habilidad

```
not-a-vibe-coder/
├── SKILL.md                 # Flujo de trabajo y definición de los 8 documentos
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [plan-writing](../plan-writing/README.md) - Estructuración y redacción de planes técnicos.
- [brainstorming](../brainstorming/README.md) - Aclaración e ideación de requerimientos vagos.
- [vibe-code-auditor](../vibe-code-auditor/README.md) - Auditorías post-desarrollo en MVPs rápidos.
