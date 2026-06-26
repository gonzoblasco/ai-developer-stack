# typescript-expert

Skill avanzada en TypeScript que abarca programación a nivel de tipos (type-level programming), optimización de rendimiento de compilación, gestión de monorepositorios y migraciones seguras.

## Resumen

Esta skill proporciona estrategias técnicas para resolver problemas de tipado complejos, errores del compilador de TypeScript (como recursiones excesivas o tipos innombrables), depuración de resolución de módulos y configuración de herramientas modernas como Biome, ESLint y Turborepo/Nx.

**Insight Clave:** Mantén el compilador estricto por defecto activando reglas como `noUncheckedIndexedAccess`. Para evitar la fatiga y lentitud del compilador en bases de código grandes, prefiere el uso de `interface` sobre intersecciones de tipos (`&`) y optimiza el proceso de compilación con `skipLibCheck: true`.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para conocer las pautas de diagnóstico y los árboles de decisión de herramientas.
2. **Validá** los tipos de tu proyecto usando la verificación rápida:
   ```bash
   npx tsc --noEmit
   ```
3. **Analizá** el rendimiento del compilador si encuentras retrasos significativos en tu editor:
   ```bash
   npx tsc --extendedDiagnostics
   ```
4. **Implementá** tipos nominales (*Branded Types*) para proteger los límites de tu dominio y evitar la obsesión por primitivos.
5. **Escribí** test de tipos estáticos en tus librerías usando `expectTypeOf` de Vitest.

## Qué Incluye

### Documentación Core y Referencias

- **[SKILL.md](SKILL.md)** - Guía metodológica exhaustiva sobre programación a nivel de tipos, configuración de tsconfig, rendimiento de compilación, depuración y checklists de revisión de código.

### Recursos Técnicos y Ejemplos (Referencias en `references/` y `examples/`)

- **[advanced-types.md](references/advanced-types.md)** - Guía de tipos condicionales, recursivos e inferencia avanzada.
- **[tsconfig-strict.json](references/tsconfig-strict.json)** - Plantilla de configuración de compilador strict-first recomendada para producción.
- **[utility-types.ts](references/utility-types.ts)** - Ejemplos de utilidades de tipo personalizadas.
- **[migration.md](references/migration.md)** - Estrategia para migrar de JavaScript a TypeScript de forma incremental.
- **[build-perf.md](references/build-perf.md)** - Pautas para acelerar los tiempos de compilación de `tsc`.
- **[checklist.md](references/checklist.md)** - Lista de control de revisión de código orientada a TypeScript.
- **[debugging.md](references/debugging.md)** - Comandos y técnicas para depurar problemas de resolución de módulos y tracing de compilación.
- **[type-test.ts](examples/type-test.ts)** - Ejemplos de aserciones de prueba sobre tipos complejos.

### Scripts de Diagnóstico

- **[ts_diagnostic.py](scripts/ts_diagnostic.py)** - Script para inspeccionar y reportar cuellos de botella de rendimiento y advertencias en la configuración de TypeScript del proyecto.

## Estructura

```
typescript-expert/
├── SKILL.md                  # Pautas de TypeScript avanzadas
├── scripts/                  # Scripts de diagnóstico del compilador
├── examples/                 # Ejemplos de código y type tests
└── references/               # Guías detalladas de tsconfig, tipos y migraciones
```

## Skills Relacionadas

- **`javascript-mastery`** - Para dominar las bases dinámicas de ejecución sobre las que opera TypeScript.
- **`nestjs-expert`** - Para la aplicación práctica de decoradores y tipado estricto en el backend.
- **`prisma-expert`** - Para la integración de modelos de base de datos tipados de extremo a extremo.
