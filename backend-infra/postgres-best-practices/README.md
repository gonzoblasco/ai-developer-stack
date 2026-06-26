# Postgres Best Practices - Guía del Colaborador

Este repositorio contiene reglas de optimización de rendimiento de Postgres adaptadas para agentes de IA y LLMs.

## Inicio Rápido

```bash
# Instalar dependencias
cd packages/postgres-best-practices-build
npm install

# Validar reglas existentes
npm run validate

# Compilar AGENTS.md
npm run build
```

## Crear una Nueva Regla

1. **Elegí un prefijo de sección** basado en la categoría:
   - `query-` Rendimiento de Consultas (CRÍTICO)
   - `conn-` Gestión de Conexiones (CRÍTICO)
   - `security-` Seguridad y RLS (CRÍTICO)
   - `schema-` Diseño de Esquemas (ALTO)
   - `lock-` Concurrencia y Bloqueos (MEDIO-ALTO)
   - `data-` Patrones de Acceso a Datos (MEDIO)
   - `monitor-` Monitoreo y Diagnóstico (BAJO-MEDIO)
   - `advanced-` Características Avanzadas (BAJO)

2. **Copiá la plantilla**:
   ```bash
   cp rules/_template.md rules/query-nombre-de-tu-regla.md
   ```

3. **Completá el contenido** siguiendo la estructura de la plantilla.

4. **Validá y compilá**:
   ```bash
   npm run validate
   npm run build
   ```

5. **Revisá** el archivo `AGENTS.md` generado.

## Estructura del Repositorio

```
skills/postgres-best-practices/
├── SKILL.md           # Manifiesto de skill orientado al agente
├── AGENTS.md          # [GENERADO] Documento compilado de reglas
├── README.md          # Este archivo
├── metadata.json      # Versión y metadatos
└── rules/
    ├── _template.md      # Plantilla de regla
    ├── _sections.md      # Definiciones de secciones
    ├── _contributing.md  # Pautas de escritura
    └── *.md              # Reglas individuales

packages/postgres-best-practices-build/
├── src/               # Código fuente del sistema de compilación
├── package.json       # Scripts de NPM
└── test-cases.json    # [GENERADO] Artefactos de prueba
```

## Estructura del Archivo de Regla

Consultá `rules/_template.md` para ver la plantilla completa. Elementos clave:

````markdown
---
title: Título claro y orientado a la acción
impact: CRITICAL|HIGH|MEDIUM-HIGH|MEDIUM|LOW-MEDIUM|LOW
impactDescription: Beneficio cuantificado (ej: "10-100x más rápido")
tags: palabras clave, relevantes
---

## [Título]

[Explicación de 1 o 2 oraciones]

**Incorrecto (descripción):**

```sql
-- Comentario explicando qué está mal
[Ejemplo de SQL malo]
```
````

**Correcto (descripción):**

```sql
-- Comentario explicando por qué esto es mejor
[Ejemplo de SQL bueno]
```

```
## Pautas de Escritura

Consultá `rules/_contributing.md` para obtener pautas detalladas. Principios clave:

1. **Mostrá transformaciones concretas**: "Cambiá X por Y", evitá consejos abstractos.
2. **Estructura error-first**: Mostrá el problema antes de la solución.
3. **Cuantificá el impacto**: Incluí métricas específicas (10x más rápido, 50% más chico).
4. **Ejemplos autocontenidos**: SQL completo y ejecutable.
5. **Nombres semánticos**: Usá nombres significativos (usuarios, email) en lugar de genéricos (tabla1, col1).

## Niveles de Impacto

| Nivel | Mejora | Ejemplos |
|-------|--------|----------|
| CRITICAL | 10-100x | Falta de índices, agotamiento de conexiones |
| HIGH | 5-20x | Tipos de índice incorrectos, particionamiento deficiente |
| MEDIUM-HIGH | 2-5x | Consultas N+1, optimización de RLS |
| MEDIUM | 1.5-3x | Índices redundantes, estadísticas desactualizadas |
| LOW-MEDIUM | 1.2-2x | Ajuste de VACUUM, retoques de configuración |
| LOW | Incremental | Patrones avanzados, casos borde |
```
