# database-design

Skill enfocada en la toma de decisiones, arquitectura de esquemas, estrategias de indexación y optimización de bases de datos.

## Resumen

Esta skill proporciona guías teóricas y árboles de decisión para seleccionar el motor de base de datos adecuado (PostgreSQL, SQLite, Neon, Turso), elegir el ORM ideal (Prisma, Drizzle, Kysely), diseñar esquemas normalizados y estructurar estrategias de indexación para garantizar un alto rendimiento.

**Insight Clave:** No uses PostgreSQL para todo por inercia. Evalúa las necesidades del despliegue y los patrones de lectura/escritura; para proyectos simples o serverless, SQLite, Turso o Neon pueden resultar significativamente más eficientes.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender el mapa de contenidos y los anti-patrones.
2. **Consultá** la documentación específica en `docs/` según el área en la que estés trabajando (diseño, migraciones, optimización).
3. **Validá** la calidad y consistencia del esquema de tu base de datos corriendo el validador:
   ```bash
   python scripts/schema_validator.py <archivo_de_esquema_o_proyecto>
   ```

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía de decisiones iniciales, checklists y principios core.

### Guías de Diseño y Decisión (Documentación en `docs/`)

- **[database-selection.md](docs/database-selection.md)** - Cuándo usar PostgreSQL tradicional frente a bases de datos serverless (Neon, Turso) o SQLite local.
- **[orm-selection.md](docs/orm-selection.md)** - Comparación objetiva y árboles de decisión entre Prisma, Drizzle ORM y Kysely.
- **[schema-design.md](docs/schema-design.md)** - Principios de normalización, llaves primarias (UUID vs CUID vs Autoincremental) y modelado de relaciones.
- **[indexing.md](docs/indexing.md)** - Tipos de índices (B-Tree, GIN), índices compuestos, cubrientes y parciales.
- **[optimization.md](docs/optimization.md)** - Análisis de planes de ejecución (`EXPLAIN ANALYZE`), detección y mitigación de consultas N+1 y optimización de queries.
- **[migrations.md](docs/migrations.md)** - Estrategias de migraciones seguras y sin downtime en producción.

### Scripts

- **[schema_validator.py](scripts/schema_validator.py)** - Validador automático de esquemas de bases de datos para identificar malas prácticas y advertencias de rendimiento.

## Estructura

```
database-design/
├── SKILL.md                  # Mapa de lectura y reglas generales
├── scripts/                  # Scripts de validación
└── docs/                     # Documentación en profundidad por tema
```

## Skills Relacionadas

- **`postgres-best-practices`** - Para pautas específicas y avanzadas del motor PostgreSQL.
- **`prisma-expert`** - Para implementar el esquema y consultas usando Prisma ORM.
- **`api-patterns`** - Para estructurar respuestas paginadas alineadas con el diseño de la base de datos.
