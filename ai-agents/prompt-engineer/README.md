# prompt-engineer

Skill para optimizar y transformar prompts informales de usuario en instrucciones altamente eficientes utilizando múltiples frameworks de ingeniería de prompts.

## Resumen

Esta skill opera silenciosamente ("magic mode") para analizar la intención del usuario, detectar la complejidad de la tarea y seleccionar de manera inteligente el framework de prompt engineering óptimo (como RTF, RISEN, Chain of Thought o RODES) para entregar un prompt estructurado y listo para su uso.

**Insight Clave:** La skill se enfoca en entregar resultados directos en formato Markdown sin abrumar al usuario final con explicaciones teóricas o jerga de frameworks.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la matriz de selección de frameworks y las reglas del "magic mode".
2. **Proporcioná** un prompt básico o vago (por ejemplo: *"ayudame a programar en Python"* o *"cómo le pido a una IA que analice este reporte"*).
3. **Obtené** un prompt optimizado y estructurado de forma instantánea en un bloque de código Markdown sin explicaciones redundantes.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Lógica de análisis de intención, matriz de frameworks y reglas críticas de formato.

## Matriz de Frameworks Soportados

La skill selecciona el framework ideal según la naturaleza de tu petición:

*   **RTF (Role-Task-Format):** Ideal para tareas basadas en roles y formatos de salida específicos.
*   **Chain of Thought (CoT):** Para tareas de depuración o lógica matemática que requieran razonamiento paso a paso.
*   **RISEN (Role-Instructions-Steps-Endgoal-Narrowing):** Para planificar proyectos complejos y estructurados.
*   **RODES (Role-Objective-Details-Examples-Sensecheck):** Para análisis y diseño técnico riguroso.
*   **Chain of Density (CoD):** Optimización y refinamiento iterativo de resúmenes.
*   **RACE (Role-Audience-Context-Expectation):** Redacción de mensajes orientados a audiencias específicas.
*   **GROW, SOAP, CLEAR, RISE, STAR:** Frameworks especializados en coaching, documentación médica/técnica, establecimiento de metas y análisis de casos.

## Reglas Críticas del Workflow

- **Sin Meta-Comentarios:** El agente no debe justificar la elección del framework ni agregar textos aclaratorios previos o posteriores.
- **Formato Limpio:** El output debe ser exclusivamente un bloque de código Markdown con el prompt optimizado.
- **Preguntas Limitadas:** Si la intención es muy ambigua, se permite un máximo de 3 preguntas aclaratorias consolidadas en una sola interacción.

## Estructura

```
prompt-engineer/
└── SKILL.md                  # Reglas del pipeline de optimización
```

## Skills Relacionadas

- **`prompt-mastery`** - Para dominar técnicas de prompts a nivel de arquitectura de sistema, prevención de inyecciones y estructuración de roles avanzados.
