# react-patterns

Skill de referencia para el diseño de componentes, composición avanzada y patrones arquitectónicos en aplicaciones de producción basadas en React (incluyendo React 19 y TypeScript).

## Resumen

Esta skill proporciona las bases para diseñar componentes limpios y predecibles. Cubre la categorización de componentes (Server, Client, Presentational, Container), reglas de extracción de custom hooks, patrones de composición avanzada (como *Compound Components*), novedades de React 19 (`useActionState`, `useOptimistic`), optimizaciones de renderizado y manejo seguro de errores con límites de error (*Error Boundaries*).

**Insight Clave:** La composición prevalece sobre la herencia en React. Mantén tus componentes pequeños, con una única responsabilidad, y pasa datos hacia abajo mediante propiedades (*props down*) mientras propagas eventos hacia arriba (*events up*).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la matriz de tipos de componentes y las novedades de React 19.
2. **Consultá** la sección de *State Management Selection* para ubicar el estado en el nivel idóneo de tu aplicación (useState, Context o Zustand).
3. **Implementá** patrones de Compound Components (como pestañas o acordeones) para desacoplar el estado y proveer layouts flexibles.
4. **Evitá** optimizaciones prematuras; utiliza el React Profiler en tus DevTools para diagnosticar cuellos de botella antes de memorizar con `useMemo` o `useCallback`.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía de diseño de componentes, reglas de hooks, patrones de React 19, composición flexible y listas de control de anti-patrones (como el uso de índices como llaves - `keys`).

## Patrones Destacados

*   **Compound Components:** Composición donde un componente padre administra un contexto y sus hijos lo consumen transparentemente (ej: `Tabs` y `Tab`).
*   **React 19 Hooks:** Patrones para optimizar interfaces interactivas asíncronas con `useOptimistic` (actualizaciones optimistas en el UI) y `useActionState` para flujos de formularios.
*   **Tipado con TypeScript:** Criterios claros para tipar props de componentes usando Interfaces, niños usando `ReactNode`, y eventos interactivos.

## Estructura

```
react-patterns/
└── SKILL.md                  # Manual de patrones de diseño React
```

## Skills Relacionadas

- **`frontend-dev-guidelines`** - Para conocer la estructura de carpetas local del proyecto.
- **`react-state-management`** - Para profundizar en librerías de gestión de estado global y del servidor.
- **`react-best-practices`** - Para aplicar las directivas de rendimiento recomendadas por Vercel.
