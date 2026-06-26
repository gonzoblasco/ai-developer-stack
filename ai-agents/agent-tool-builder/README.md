# agent-tool-builder

Skill integral para diseñar herramientas de agentes de IA siguiendo las mejores prácticas.

## Resumen

Esta skill te guía en la creación de herramientas bien diseñadas para agentes de IA, enfocándose en el diseño de JSON Schema, descripciones claras, manejo de errores estructurado y el estándar MCP.

**Insight Clave:** El LLM nunca ve tu código, solo el esquema y la descripción. Hacelos transparentes y legibles.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para obtener una guía completa.
2. **Usá** los scripts para validar y generar:
   ```bash
   python scripts/validate_tool_schema.py tu_herramienta.json
   python scripts/generate_tool_template.py --name mi_herramienta --type mcp --params "query:string"
   ```
3. **Consultá** las plantillas y checklists mientras construís.
4. **Profundizá** en las referencias para temas avanzados.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Skill principal (814 líneas)
- **[walkthrough.md](walkthrough.md)** - Documentación completa del proceso de reescritura
- **[implementation_plan.md](implementation_plan.md)** - Planificación de TDD
- **[task.md](task.md)** - Seguimiento del proceso

### Herramientas Prácticas

- **[validate_tool_schema.py](scripts/validate_tool_schema.py)** - Validar esquemas contra las mejores prácticas
- **[generate_tool_template.py](scripts/generate_tool_template.py)** - Generar código base (boilerplate)

### Plantillas y Checklists

- **[mcp-tool-template.py](assets/templates/mcp-tool-template.py)** - Plantilla completa de herramienta MCP
- **[tool-schema-template.json](assets/templates/tool-schema-template.json)** - Plantilla de JSON Schema
- **[tool-quality-checklist.md](assets/checklists/tool-quality-checklist.md)** - Checklist de revisión de calidad
- **[tool-design-decisions.md](assets/decision-trees/tool-design-decisions.md)** - Diagramas de flujo de decisión

### Temas Profundos

- **[json-schema-deep-dive.md](references/json-schema-deep-dive.md)** - Patrones avanzados de JSON Schema
- **[mcp-standard-guide.md](references/mcp-standard-guide.md)** - Guía de implementación de MCP
- **[error-handling-patterns.md](references/error-handling-patterns.md)** - Estrategias de manejo de errores

## Ejemplos de Uso

### Validar el Esquema de una Herramienta

```bash
python scripts/validate_tool_schema.py mi_esquema_de_herramienta.json
```

Salida:

```
✅ ¡El esquema es válido y sigue todas las mejores prácticas!
```

o bien:

```
❌ ERRORES (deben corregirse):
  - El parámetro 'query' no tiene descripción
 
⚠️  ADVERTENCIAS (deberían corregirse):
  - La descripción es demasiado corta (15 palabras, mínimo 20)
 
💡 SUGERENCIAS (opcional):
  - Agregar ejemplos para el parámetro complejo 'filters'
```

### Generar una Nueva Herramienta

```bash
python scripts/generate_tool_template.py \
  --name search_documents \
  --type mcp \
  --params "query:string,limit:integer,filters:object"
```

Genera el boilerplate completo con el esquema, el código y la plantilla de descripción.

## Principios Clave

1. **El LLM ve el esquema + la descripción, no el código** → Hacelos claros, específicos y legibles.
2. **Descripción > Implementación** → Una herramienta con código perfecto pero descripción vaga fallará.
3. **Los errores deben guiar la recuperación** → No te limites a reportar la falla, sugerí cómo solucionarlo.
4. **Sé específico con los tipos** → Usá enums, restricciones y ejemplos siempre que sea posible.
5. **Probá contra escenarios reales** → Caso feliz (happy path) + casos borde + recuperación de errores.

## Estructura

```
agent-tool-builder/
├── SKILL.md                  # Contenido principal (814 líneas)
├── README.md                 # Este archivo
├── walkthrough.md            # Documentación del proceso
├── implementation_plan.md    # Planificación de TDD
├── task.md                   # Seguimiento
│
├── scripts/                  # Herramientas de validación y generación
│   ├── validate_tool_schema.py
│   └── generate_tool_template.py
│
├── assets/
│   ├── templates/            # Plantillas de código y esquemas
│   ├── checklists/           # Checklists de calidad
│   └── decision-trees/       # Diagramas de flujo de decisión
│
└── references/               # Documentación en profundidad
    ├── json-schema-deep-dive.md
    ├── mcp-standard-guide.md
    └── error-handling-patterns.md
```

## Skills Relacionadas

- **`mcp-builder`** - Para diseñar servidores MCP completos
- **`autonomous-agent-expert`** - Para bucles de agentes y patrones de integración de herramientas
- **`backend-expert`** - Para implementar herramientas en Node.js/Express
- **`prompt-mastery`** - Para optimizar las descripciones de las herramientas y los prompts

## Nota Meta

Esta skill **ejemplifica sus propios principios**:

- El script de validación devuelve errores estructurados (lo que enseña).
- Las plantillas demuestran las mejores prácticas (divulgación progresiva).
- Los scripts tienen descripciones y manejo de errores claros (meta-recursivo).

Una skill sobre diseño de herramientas que utiliza herramientas para enseñar diseño de herramientas. 🪞

---

**Recordá:** Cada herramienta que diseñás es un contrato entre el LLM y el mundo. Hacela clara, hacela específica, hacela útil.
