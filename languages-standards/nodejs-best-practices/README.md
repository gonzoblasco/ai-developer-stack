# nodejs-best-practices

Skill enfocada en la toma de decisiones, arquitectura del lado del servidor, seguridad y buenas prácticas de desarrollo en el entorno de ejecución Node.js (y alternativas modernas).

## Resumen

Esta skill proporciona principios rectores para estructurar proyectos Node.js de forma escalable. Ofrece árboles de decisión para la selección de frameworks (Hono, Fastify, NestJS, Express), optimización asíncrona, prevención del bloqueo del Event Loop, estrategias de validación en fronteras, manejo centralizado de errores y seguridad de infraestructura.

**Insight Clave:** No uses el mismo framework para todo por defecto. Elige la herramienta según el entorno de despliegue: usa Hono para Edge/Serverless por su nulo cold-start, Fastify para APIs de alto rendimiento, o NestJS para grandes aplicaciones empresariales estructuradas.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para repasar el árbol de decisión de frameworks y la matriz de selección.
2. **Estructurá** tus aplicaciones bajo una arquitectura de 3 capas independientes (Controlador, Servicio y Repositorio) para asegurar la testabilidad y desacoplamiento.
3. **Validá** las entradas de datos en la frontera de tus APIs usando esquemas con inferencia de tipos como Zod.
4. **Implementá** un middleware de manejo centralizado de errores para formatear las respuestas de cara al cliente de forma segura (sin exponer stack traces internos).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía de decisiones que abarca:
  1. Árbol de decisión y comparación de frameworks.
  2. Consideraciones del runtime (Node.js vs Bun vs Deno, ESM vs CommonJS, Strip Types de Node 22).
  3. Arquitectura en capas.
  4. Gestión y tipificación de errores.
  5. Asincronía e impacto en el Event Loop (I/O-bound vs CPU-bound).
  6. Bibliotecas de validación (Zod, Valibot, ArkType).
  7. Checklist de seguridad y testing.
  8. Anti-patrones de producción.

## Matriz de Selección de Frameworks

| Framework | Caso de Uso Ideal | Fortalezas |
| :--- | :--- | :--- |
| **Hono** | Serverless / Edge (Cloudflare Workers, Vercel) | Peso pluma, inicio en frío ultrarrápido, TS nativo. |
| **Fastify** | APIs REST tradicionales de alta carga | Rendimiento extremo, plugin-system robusto, schemas rápidos. |
| **NestJS** | Aplicaciones corporativas y estructuradas | Inyección de dependencias nativa, modularidad forzada, decoradores. |
| **Express** | Proyectos heredados o muy simples | Máximo ecosistema de middlewares de la comunidad. |

## Estructura

```
nodejs-best-practices/
└── SKILL.md                  # Pautas de arquitectura y desarrollo Node.js
```

## Skills Relacionadas

- **`clean-code`** y **`software-architecture`** - Para la aplicación de modularidad y nomenclatura limpia de archivos.
- **`javascript-testing-patterns`** - Para implementar el pipeline de pruebas unitarias y de integración sobre la arquitectura en capas.
