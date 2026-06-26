# modern-javascript-patterns

Skill práctica enfocada en la aplicación de características de JavaScript moderno (ES6+), patrones de programación funcional y recetas de refactorización de código heredado (legacy).

## Resumen

Esta skill sirve como puente práctico complementando los conceptos de `javascript-mastery`. Proporciona patrones listos para usar en migración asíncrona, inmutabilidad de datos, tuberías de transformación de arrays, currying, mapeos condicionales y optimizaciones de rendimiento a través de memoización, *debounce* y *throttle*.

**Insight Clave:** Migrar de callbacks secuenciales a llamadas asíncronas concurrentes con `Promise.all` e implementar guardas de retorno temprano (*early returns*) en lugar de anidaciones profundas mejora drásticamente la velocidad del software y la legibilidad del código.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para repasar la tabla comparativa de refactorización rápida y recetas.
2. **Consultá** la sección de *Async Migration Patterns* al convertir viejas llamadas basadas en callbacks hacia async/await.
3. **Refactorizá** condicionales `if/else` extensos reemplazándolos por tablas de mapeo estructurado (*lookups*).
4. **Implementá** flujos de procesamiento funcionales usando composición (`pipe`/`compose`) e inmutabilidad (`...spread`).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía práctica de refactorización agrupada en 5 áreas:
  1. Patrones de migración asíncrona y concurrencia.
  2. Patrones de programación funcional (inmutabilidad, tuberías, composición, currying).
  3. Patrones de arrays y objetos (desestructuración, construcción dinámica, optional chaining).
  4. Recetas de refactorización (lookups en vez de if-else, cláusulas de guarda, constantes nominales).
  5. Patrones de rendimiento (memoización, debounce, throttle, inicialización perezosa).

## Recetario de Refactorización Rápida

| Patrón Legacy | Reemplazo Moderno |
| :--- | :--- |
| **Callbacks** | `async/await` con control de errores por bloques `try/catch`. |
| **Awaits Secuenciales** | `Promise.all([p1, p2])` para resolver promesas en paralelo. |
| **Mutación de Objetos** | Copia inmutable mediante spreads `{ ...objeto, nuevoValor }`. |
| **Concatenación** | Plantillas de texto (Template literals: `` `Hello ${user}` ``). |
| **Nidación if-else** | Cláusulas de guarda tempranas (*Guard clauses*). |
| **Múltiples if/else if** | Tablas hash u objetos de mapeo (`STATUS_LOOKUP[status]`). |

## Estructura

```
modern-javascript-patterns/
└── SKILL.md                  # Recetario de refactorización y patrones modernos
```

## Skills Relacionadas

- **`javascript-mastery`** - Para consultar la teoría base detrás de las clausuras, prototipos y el Event Loop.
- **`clean-code`** - Para alinearse con las pautas deUncle Bob sobre tamaño de métodos e intenciones de variables.
