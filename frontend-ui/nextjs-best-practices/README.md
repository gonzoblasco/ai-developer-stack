# nextjs-best-practices

Skill enfocada en la arquitectura, toma de decisiones y mejores prácticas para el desarrollo en Next.js (App Router).

## Resumen

Esta skill proporciona las directrices para estructurar aplicaciones Next.js. Cubre el árbol de decisión para separar Server Components y Client Components, la lógica de recuperación y almacenamiento en caché de datos (ISR, Dynamic, Static), convenciones de enrutamiento basado en archivos (loading, error, layout), APIs internas (Route Handlers) y optimización de SEO y Web Vitals.

**Insight Clave:** El servidor es el entorno por defecto en Next.js. Inicia siempre con Server Components para la carga de datos y layouts estáticos, y limita el uso de Client Components (`'use client'`) estrictamente a la interactividad (estados locales, eventos e interactividad).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la división Server vs Client y las capas de caché de Next.js.
2. **Estructurá** tus páginas usando las convenciones de archivos de Next.js (`layout.tsx`, `page.tsx`, `loading.tsx`, `error.tsx`).
3. **Implementá** mutaciones utilizando Server Actions (`'use server'`) con validación de tipos e inputs (ej: con Zod).
4. **Validá** que las imágenes utilicen el componente `next/image` con prioridades y blur placeholders para proteger el Cumulative Layout Shift (CLS).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Flujos de arquitectura de componentes, estrategias de recuperación, ruteo avanzado (intercepting/parallel routes), Server Actions y matrices de anti-patrones.

## Capas y Conceptos Destacados

*   **Server Actions:** Mutaciones directas cliente-servidor seguras e integradas nativamente con el sistema de revalidación (`revalidatePath`).
*   **Optimizaciones SEO:** Generación de metadatos dinámicos por ruta (`generateMetadata`), canonicals y OG tags.
*   **Arquitectura de Caché:** Request Memoization, Data Cache y Full Route Cache para control de tiempos de revalidación.

## Estructura

```
nextjs-best-practices/
└── SKILL.md                  # Manual de desarrollo en Next.js App Router
```

## Skills Relacionadas

- **`frontend-dev-guidelines`** - Para alinearse con las pautas de Suspense-first locales.
- **`nextjs-production-debugger`** - Para solucionar problemas de hidratación y caídas en producción.
- **`react-best-practices`** - Para optimizar bundlers y cascadas de peticiones.
