# react-best-practices

Guía de optimización de rendimiento avanzada para aplicaciones React y Next.js mantenida por Vercel, que clasifica 45 reglas críticas en 8 niveles de prioridad.

## Resumen

Esta skill reúne la doctrina de rendimiento de Vercel. Aborda desde la eliminación de cascadas de red (*waterfalls*) asíncronas, optimización de tamaño de bundles mediante importaciones dinámicas, control del ciclo de vida en el servidor (React cache, serialización mínima de props), hasta la reducción de re-renderizados innecesarios en el cliente e inyección de estándares de rendimiento en JavaScript nativo.

**Insight Clave:** La optimización es crítica para la retención de usuarios. Estructurar peticiones en paralelo con `Promise.all`, evitar archivos barril (`index.ts` que exportan todo un módulo) para reducir el bundle, y usar `startTransition` para actualizaciones no urgentes previene bloqueos de la interfaz.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la priorización de las 8 categorías de reglas.
2. **Consultá** la versión compilada de reglas en [AGENTS.md](AGENTS.md) (si está disponible) antes de refactorizar componentes pesados.
3. **Evitá** esperas de red secuenciales moviendo los `await` directamente a las ramas de código donde se consumen los datos, o disparando consultas en paralelo.
4. **Implementá** componentes dinámicos (`next/dynamic`) para dividir el código y diferir la carga de librerías de analíticas o modales complejos.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Índice priorizado de las 45 reglas clasificadas por prefijos (`async-`, `bundle-`, `server-`, `client-`, `rerender-`, `rendering-`, `js-`, `advanced-`).
- **[AGENTS.md](AGENTS.md)** - Manual compilado con el detalle extendido de cada regla.

## Clasificación de Reglas por Impacto

1.  **Eliminación de Waterfalls (Crítico - `async-`):** Paralelización y streaming mediante límites de Suspense.
2.  **Optimización de Bundle (Crítico - `bundle-`):** Dynamic imports, evitar importaciones barril y carga diferida de scripts de terceros.
3.  **Rendimiento del Servidor (Alto - `server-`):** Deduplicación de peticiones con `React.cache()` y des-serialización compacta al cliente.
4.  **Rendimiento del Cliente (Medio-Alto - `client-`):** Reuso de event listeners globales y deduplicación con SWR/React Query.
5.  **Optimización de Re-renderizados (Medio - `rerender-`):** Memorización con `useMemo`/`useCallback` y inicialización perezosa de estados (`useState(() => value)`).

## Estructura

```
react-best-practices/
├── SKILL.md                  # Índice y priorización de reglas Vercel
└── AGENTS.md                 # Documento completo con las 45 reglas expandidas
```

## Skills Relacionadas

- **`nextjs-best-practices`** - Para alinearse con las pautas de arquitectura del App Router.
- **`frontend-dev-guidelines`** - Para cumplir con las directivas de Suspense locales.
- **`nextjs-production-debugger`** - Para depurar caídas de rendimiento o hidratación en producción.
