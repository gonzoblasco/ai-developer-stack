# prompt-mastery

Guía avanzada de ingeniería de prompts, patrones de diseño para LLMs, sistemas de plantillas y mitigación de vulnerabilidades.

## Resumen

Esta skill aborda la creación de prompts con el rigor de la ingeniería de software. Ofrece arquitecturas para prompts de sistema, patrones avanzados de pocos ejemplos (few-shot), cadenas de pensamiento (chain-of-thought) y checklists sistemáticos de aseguramiento de la calidad.

**Insight Clave:** Los mejores prompts no dependen de la intuición; son específicos, contextualizados, muestran ejemplos, manejan de forma segura las entradas de usuario y se validan iterativamente.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la estructura base recomendada para un prompt.
2. **Aplicá** el patrón estructural estándar para System Prompts:
   ```markdown
   [Rol] → [Contexto] → [Instrucciones] → [Restricciones] → [Ejemplos] → [Formato de Salida]
   ```
3. **Revisá** la biblioteca de ejemplos prácticos en [examples/library.md](examples/library.md).
4. **Consultá** la lista de verificación en [references/checklists.md](references/checklists.md) antes de publicar un prompt de sistema.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Estructura core de prompts y recursos integrados.

### Técnicas y Ejemplos

- **[techniques.md](references/techniques.md)** - Guía sobre técnicas avanzadas: *Few-Shot Learning*, *Chain-of-Thought*, *Self-Consistency* y *Prompt Chaining*.
- **[library.md](examples/library.md)** - Biblioteca de plantillas listas para usar según el rol deseado (Experto, Revisor, Diseñador, etc.).
- **[checklists.md](references/checklists.md)** - Checklist de control de calidad, anti-patrones comunes y mitigación de inyecciones de prompts (*Prompt Injection*).

## Principios Clave de Calidad

*   **Evitar Instrucciones Vagas:** En lugar de *"Sé conciso"*, utiliza *"Escribe la respuesta en menos de 3 oraciones"*.
*   **Mitigación de Anti-patrones:** Evitar el *"Kitchen Sink"* (amontonar reglas no relacionadas) y enfocar el prompt en una única tarea estructurada.
*   **Seguridad:** Implementar delimitadores de texto (por ejemplo, `"""` o XML tags) para aislar datos del usuario y prevenir fugas de instrucciones.

## Estructura

```
prompt-mastery/
├── SKILL.md                  # Pautas fundamentales de diseño
├── references/               # Técnicas de optimización y checklists de QA
└── examples/                 # Biblioteca de plantillas y ejemplos prácticos
```

## Skills Relacionadas

- **`prompt-engineer`** - Para la traducción automatizada y silenciosa de consultas cotidianas de usuarios mediante frameworks predefinidos.
- **`ai-agents-architect`** - Para estructurar prompts orientados a loops autónomos y lógica agéntica.
