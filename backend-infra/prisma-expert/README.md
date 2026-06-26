# prisma-expert

Skill experta en Prisma ORM para el diseño de esquemas, migraciones de bases de datos y optimización de consultas en PostgreSQL, MySQL y SQLite.

## Resumen

Esta skill proporciona diagnósticos, mejores prácticas de modelado de datos y soluciones estructuradas para el desarrollo con Prisma. Abarca desde la prevención de consultas lentas y problemas de N+1, hasta el manejo de la concurrencia mediante transacciones y la gestión segura de conexiones en entornos tradicionales y serverless.

**Insight Clave:** Nunca uses `prisma migrate dev` en producción (usa siempre `prisma migrate deploy`). Evita el sobreprocesamiento de datos e ineficiencia de red seleccionando únicamente los campos requeridos mediante `select` en lugar de incluir relaciones completas con `include` por defecto.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para conocer las pautas de validación y la matriz de diagnóstico de errores comunes.
2. **Validá** la sintaxis y consistencia de tu archivo de esquema:
   ```bash
   npx prisma validate
   npx prisma format
   ```
3. **Consultá** la sección de optimización de consultas para solucionar problemas de lentitud de red o cuellos de botella.
4. **Implementá** el patrón de conexión global seguro para entornos serverless (como Next.js/Vercel) para prevenir el agotamiento de sockets de base de datos.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía técnica exhaustiva que cubre modelado de esquemas, flujos seguros de migración, optimización de queries, límites de pool de conexión y patrones transaccionales.

## Patrones Destacados en la Skill

### Modelado de Esquemas Limpios
Uso de mapeo de nombres de tablas y llaves con `@map` y `@@map`, definición de acciones referenciales (`onDelete: Cascade`), e índices explícitos (`@@index`).

### Prevención de Consultas N+1
Ejemplos de cómo pasar de consultas anidadas ineficientes a cargas conjuntas (`include`), selección de campos específicos (`select`) y la caída a consultas nativas seguras con `prisma.$queryRaw`.

### Conectores Serverless Seguros
Uso de un singleton global en entornos Node.js de desarrollo para evitar la recreación de clientes en cada recarga de código (hot-reloading).

### Transacciones Avanzadas
Transacciones secuenciales básicas frente a transacciones interactivas con control de tiempos de espera (`timeout`), niveles de aislamiento y control de concurrencia optimista mediante versiones.

## Estructura

```
prisma-expert/
└── SKILL.md                  # Contenido técnico principal
```

## Skills Relacionadas

- **`database-design`** - Para la toma de decisiones conceptuales sobre bases de datos y ORMs.
- **`postgres-best-practices`** - Para optimizaciones específicas del motor PostgreSQL.
- **`nestjs-expert`** - Para implementar Prisma de manera modular dentro de NestJS.
