# meta-skill-antigravity

La meta-herramienta para crear, editar, validar y testear skills en el Antigravity Stack bajo los principios de Test-Driven Development (TDD).

## Resumen

Esta skill unifica la disciplina TDD de desarrollo de software con la ingeniería de prompts y la gestión del contexto. Proporciona flujos metodológicos para crear nuevas habilidades para agentes de IA asegurando que resuelvan fallas reales verificadas mediante tests baseline previos (RED Phase).

**Insight Clave:** El contexto de un agente es un bien público escaso. No crees una skill si puedes resolver el problema con un prompt simple, y nunca la implementes sin comprobar primero que el agente falla sin ella.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender los conceptos de *Progressive Disclosure*, *Degrees of Freedom* y el ciclo TDD agéntico.
2. **Inicializá** una nueva skill estructurada usando el script interactivo:
   ```bash
   python scripts/init_skill.py mi-nueva-skill --type [domain|guardrail|reference]
   ```
3. **Validá** las reglas de tus skills locales (como límites de líneas, frontmatter y estilo):
   ```bash
   python scripts/validate_skill.py mi-nueva-skill --validate
   ```
4. **Ejecutá** un test baseline (RED Phase) para registrar las excusas del agente antes de aplicar las contramedidas.

## Qué Incluye

### Documentación Core y Plantillas

- **[SKILL.md](SKILL.md)** - Guía metodológica principal de creación de skills.
- **[basic-skill-template.md](templates/basic-skill-template.md)** - Estructura básica de un archivo SKILL.md.
- **[discipline-skill-template.md](templates/discipline-skill-template.md)** y **[reference-skill-template.md](templates/reference-skill-template.md)** - Plantillas para skills de disciplina técnica y de referencia/conocimiento.

### Scripts de Automatización

- **[init_skill.py](scripts/init_skill.py)** - Inicializador estándar de carpetas y archivos de skills.
- **[validate_skill.py](scripts/validate_skill.py)** - Validador de conformidad del formato de skills y ejecución de baselines de test.

### Guías Avanzadas

- **[testing-methodology.md](references/testing-methodology.md)** - Metodología TDD para documentación y prompts.
- **[degrees-of-freedom.md](references/degrees-of-freedom.md)** - Cómo equilibrar la rigidez de las instrucciones frente a la flexibilidad del agente.
- **[context-efficiency.md](references/context-efficiency.md)** - Técnicas de optimización de consumo de tokens y jerarquías de archivos.
- **[cso-optimization.md](references/cso-optimization.md)** - Optimización de triggers y descripciones de metadatos de skills.

## Principios de Desarrollo de Skills

1. **Progressive Disclosure (3 Niveles):**
   * Nivel 1: Metadata (Trigger en la descripción del plugin/skill).
   * Nivel 2: SKILL.md (Instrucciones core, acotadas a < 500 líneas).
   * Nivel 3: Recursos anidados (Scripts, plantillas, referencias en demanda).
2. **The Iron Law (TDD):** Ninguna skill debe crearse sin un escenario de fallo contrastado previamente.
3. **Bulletproofing:** Mitigar racionalizaciones erróneas de los agentes usando tablas explícitas de "Excusa vs Realidad".

## Estructura

```
meta-skill-antigravity/
├── SKILL.md                  # Metodología principal
├── scripts/                  # Scripts de inicialización y validación
├── templates/                # Plantillas markdown para nuevas skills
├── references/               # Conceptos teóricos y guías avanzadas de diseño
└── examples/                 # Ejemplos paso a paso de TDD agéntico
```

## Skills Relacionadas

- **`prompt-mastery`** - Para escribir instrucciones sumamente efectivas dentro de los archivos `SKILL.md`.
- **`ai-agents-architect`** - Para comprender las implicaciones del consumo de skills en loops complejos.
