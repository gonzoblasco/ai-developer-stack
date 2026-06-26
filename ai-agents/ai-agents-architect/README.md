# ai-agents-architect

Skill especializada en diseñar y construir agentes de IA autónomos y sistemas multi-agente confiables.

## Resumen

Esta skill proporciona las bases arquitectónicas y los patrones de diseño necesarios para crear sistemas agénticos que actúen de manera autónoma pero controlable, con un enfoque en la degradación elegante, el manejo de loops infinitos y la seguridad.

**Insight Clave:** Los agentes fallan de formas inesperadas. Diseñar para el fallo controlado y la observabilidad es más importante que buscar la autonomía absoluta.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para conocer las pautas de diseño y límites recomendados.
2. **Implementá** un loop agéntico (como **ReAct** o **Plan-and-Execute**) asegurando siempre un límite estricto de iteraciones (`max_iterations`).
3. **Establecé** un sistema de memoria jerárquica para preservar el contexto de forma eficiente.
4. **Definí** límites y guardrails antes de dar control total al agente sobre herramientas destructivas.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Skill principal con directrices arquitectónicas, patrones de bucles y límites.

## Patrones de Arquitectura Clave

1. **Loop ReAct (Reason-Act-Observe):** Ciclo continuo de razonamiento, acción y observación con control estricto de iteraciones para evitar bucles infinitos.
2. **Plan-and-Execute:** Descomposición de tareas complejas en pasos, ejecución secuencial y replanificación dinámica basada en resultados intermedios.
3. **Memoria Jerárquica:** Combinación de memoria de trabajo (contexto actual), memoria episódica (interacciones pasadas) y memoria semántica (hechos persistentes) apoyada por RAG.
4. **Patrón Supervisor:** Un agente supervisor descompone, delega tareas a agentes especialistas y consolida los resultados.
5. **Recuperación por Checkpoints:** Salvaguarda del estado del agente tras cada paso exitoso para permitir la resiliencia ante caídas de entorno.

## Principios de Diseño

- **Fallo Ruidoso:** Los agentes deben fallar de forma explícita y documentada, nunca de manera silenciosa.
- **Contratos Claros:** Cada herramienta expuesta al agente debe poseer documentación, schemas JSON y ejemplos específicos.
- **Contexto Eficiente:** La memoria es para el contexto relevante; almacenar historiales crudos innecesarios degrada la calidad y aumenta costos.
- **La Planificación reduce Errores:** Pero no los elimina. Diseñá siempre mecanismos de retroalimentación (replanning).

## Estructura

```
ai-agents-architect/
└── SKILL.md                  # Contenido arquitectónico principal
```

## Skills Relacionadas

- **`rag-expert`** - Para implementar sistemas de recuperación de memoria a largo plazo.
- **`prompt-mastery`** - Para diseñar system instructions robustas.
- **`mcp-builder`** - Para conectar el agente a APIs externas mediante herramientas estandarizadas.
- **`agent-tool-builder`** - Para el diseño de schemas de herramientas individuales.
