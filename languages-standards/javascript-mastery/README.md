# javascript-mastery

Skill de referencia que consolida los conceptos esenciales de JavaScript que todo desarrollador debe dominar, inspirados en "33-js-concepts".

## Resumen

Esta skill abarca la teoría y comportamiento interno de JavaScript. Cubre desde tipos primitivos y coerción, ámbitos de variables (Scope) y clausuras (Closures), el funcionamiento del Event Loop y tareas asíncronas (`async`/`await`/Promesas), hasta programación funcional, herencia por prototipos y las características modernas de ES6+ (Destructuring, Spread/Rest, Nullish Coalescing).

**Insight Clave:** Comprender el Event Loop (el orden de ejecución de tareas sincrónicas, microtareas y macrotareas) y la diferencia entre igualdad estricta (`===`) y coerción de tipos previene la mayoría de los bugs inesperados en JavaScript.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para repasar la lista de conceptos fundamentales y la tarjeta de referencia rápida.
2. **Consultá** las reglas de asignación y enlazado dinámico del objeto `this` al diseñar métodos o utilizar arrow functions.
3. **Optimizá** tus consultas asíncronas en paralelo usando combinadores como `Promise.all` o `Promise.allSettled`.
4. **Implementá** patrones de programación funcional pura (map, filter, reduce) y currying para modularizar tus algoritmos.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía exhaustiva dividida en 7 bloques conceptuales:
  1. Fundamentos (Tipos primitivos, coerción y operadores de igualdad).
  2. Ámbito y Clausuras (Scope, Closures, Temporal Dead Zone, let/const/var).
  3. Funciones y Ejecución (Pila de llamadas, Hoisting y contexto `this`).
  4. Event Loop y Asincronía (Callbacks, Promesas y async/await).
  5. Programación Funcional (Funciones puras, HOF, Currying y Composición).
  6. Objetos y Prototipos (Herencia prototypal, Object methods, mutabilidad).
  7. JavaScript Moderno (Desestructuración, Spread/Rest, Módulos ESM, Optional chaining y Nullish coalescing).

## Tabla de Referencia Rápida

| Concepto | Regla de Oro |
| :--- | :--- |
| **Comparaciones** | Usar siempre `===` para evitar la coerción implícita indeseada. |
| **Variables** | Preferir `const` y `let` sobre `var` para respetar el block scope. |
| **Clausuras** | Aprovecharlas para encapsular variables y crear privacidad de datos. |
| **Event Loop** | Las microtareas (promesas) se ejecutan siempre antes que las macrotareas (settimeouts). |
| **this** | Su valor depende de *cómo* se invoque la función, a menos que sea una arrow function (léxico). |
| **?? vs \|\|** | El operador `??` solo evalúa `null` o `undefined`, protegiendo el `0` y `""` como válidos. |

## Estructura

```
javascript-mastery/
└── SKILL.md                  # Manual de conceptos fundamentales de JS
```

## Skills Relacionadas

- **`typescript-expert`** - Para agregar tipado estático y robusto sobre los patrones dinámicos de JavaScript.
- **`modern-javascript-patterns`** - Para aplicar estos conceptos en el diseño de patrones de software modernos.
