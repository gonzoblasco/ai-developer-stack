# mcp-builder

Guía y herramientas para crear servidores MCP (Model Context Protocol) de alta calidad en Python y TypeScript.

## Resumen

Esta skill te guía en la planificación, estructuración, desarrollo y evaluación de servidores MCP que permiten a los LLMs interactuar de forma segura y eficiente con servicios y APIs externas.

**Insight Clave:** La calidad de un servidor MCP se mide por la claridad de las descripciones de sus herramientas, su resiliencia ante errores y la optimización del tamaño de su contexto de retorno.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender el flujo de desarrollo de 4 fases (Planificación, Implementación, Testeo y Evaluación).
2. **Generá** la base del proyecto instantáneamente usando el script de andamiaje:
   ```bash
   ./scripts/scaffold.sh mi-nuevo-servidor
   ```
3. **Usá** la [Prompts Library](reference/prompts.md) para autogenerar esquemas y código de servidor.
4. **Evaluá** tu servidor creando un set de pruebas en `evaluation.xml` y corriendo el script de validación.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía principal de desarrollo y flujos de trabajo.
- **[mcp_best_practices.md](reference/mcp_best_practices.md)** - Convenciones de nomenclatura, seguridad y manejo de errores.
- **[node_mcp_server.md](reference/node_mcp_server.md)** - Guía detallada para implementaciones en TypeScript.
- **[python_mcp_server.md](reference/python_mcp_server.md)** - Guía detallada para implementaciones en Python (FastMCP).
- **[evaluation.md](reference/evaluation.md)** - Framework y metodología para validar el funcionamiento del servidor.
- **[prompts.md](reference/prompts.md)** - Biblioteca de prompts listos para usar en generación de código.

### Scripts y Código

- **[scaffold.sh](scripts/scaffold.sh)** - Automatización para inicializar proyectos MCP.
- **[connections.py](scripts/connections.py)** y **[evaluation.py](scripts/evaluation.py)** - Utilidades para testeo y evaluación de llamadas.

## Principios Clave de MCP

1. **Manejo de Errores Estricto:** Los servidores MCP nunca deben crashear. Las excepciones deben ser capturadas y devueltas como mensajes legibles en el contexto del LLM.
2. **Logs a stderr:** La comunicación de protocolo se realiza por `stdout`. Cualquier log de depuración debe escribirse obligatoriamente en `stderr`.
3. **Descripciones Detalladas:** Las herramientas necesitan descripciones detalladas de sus parámetros para evitar que el LLM cometa errores al invocarlas.
4. **Paginación y Límites de Salida:** Respuestas excesivamente grandes deben truncarse o paginarse para proteger la ventana de contexto.

## Estructura

```
mcp-builder/
├── SKILL.md                  # Flujo de trabajo principal
├── LICENSE.txt               # Licencia del proyecto
├── scripts/                  # Scripts de scaffolding y evaluación
└── reference/                # Guías técnicas de lenguaje y mejores prácticas
```

## Skills Relacionadas

- **`agent-tool-builder`** - Para el diseño minucioso de schemas JSON y parámetros individuales.
- **`ai-agents-architect`** - Para entender cómo los agentes orquestan y consumen estas herramientas.
