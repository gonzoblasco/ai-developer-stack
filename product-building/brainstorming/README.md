# Brainstorming Ideas Into Designs

Framework y flujo de facilitación para transformar ideas vagas o especificaciones iniciales en diseños de software e interfaces validados antes de comenzar cualquier codificación.

## Resumen

Esta habilidad actúa como un moderador técnico para evitar la implementación prematura y las asunciones silenciosas. Establece un proceso estructurado mediante preguntas secuenciales, análisis de requisitos no funcionales, validación de alternativas de diseño y mantenimiento de un registro de decisiones (Decision Log). Durante su ejecución, el agente tiene prohibido realizar cualquier cambio en el código del proyecto.

## Inicio Rápido

Para iniciar un proceso de clarificación de diseño:

1. **Reconocimiento del Contexto**: Analiza la documentación actual, planes y código existente del proyecto.
2. **Entendimiento Secuencial**: Formula preguntas cortas para entender el propósito, los usuarios y las restricciones.
3. **Bloqueo de Entendimiento (Understanding Lock)**: Antes de proponer soluciones técnicas, consolida un resumen de 5 a 7 puntos clave con supuestos y obtén la confirmación del usuario.

## Qué Incluye

- **Fases del Proceso**:
  - Contexto inicial (Análisis de código y planes).
  - Aclaración de idea (una pregunta a la vez).
  - Definición de requisitos no funcionales (rendimiento, escalabilidad, seguridad).
  - Bloqueo de entendimiento obligatorio.
  - Exploración de 2 a 3 enfoques de diseño y presentación incremental de la opción elegida.
- **Registro de Decisiones (Decision Log)**: Documentación de alternativas descartadas y motivos de selección.
- **Criterios de Salida**: Lista de verificación para desactivar el modo de lluvia de ideas antes de iniciar la implementación.

## Conceptos Clave

- **YAGNI (You Aren't Gonna Need It)**: Evitar la optimización prematura o el desarrollo de características especulativas.
- **Una pregunta por mensaje**: Utilizar preferentemente preguntas de opción múltiple para agilizar las decisiones del usuario sin saturar la conversación.
- **Handoff a Multi-Agent**: Si el diseño es de alto impacto o riesgo, entregar el registro de decisiones a herramientas avanzadas de brainstorming multi-agente.

## Estructura de la Habilidad

```
brainstorming/
├── SKILL.md                 # Guía y flujo del proceso de brainstorming
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [plan-writing](../plan-writing/README.md) - Escritura de planes de implementación detallados.
- [product-manager](../product-manager/README.md) - Definición de características de negocio y requerimientos de usuario.
