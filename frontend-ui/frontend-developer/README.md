# frontend-developer

Skill general para el desarrollo frontend moderno que cubre la construcción de componentes React 19, layouts responsivos, Next.js 15 App Router y patrones avanzados del ecosistema web.

## Resumen

Esta skill sirve como guía global para ingenieros frontend. Abarca capacidades de desarrollo React (RSC, Server Actions, concurrencia, hooks asíncronos), optimizaciones para Core Web Vitals (LCP, FID, CLS), integración de gestores de estado (Zustand, TanStack Query), maquetación responsiva con Tailwind, pruebas (RTL, Playwright) e implementación de accesibilidad (WCAG 2.2).

**Insight Clave:** Prioriza el rendimiento, la accesibilidad y la experiencia del usuario (UX) en partes iguales. Diseña arquitecturas de componentes modulares y mantenibles, utilizando TypeScript y tipando estrictamente las props y retornos de API.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para repasar el espectro completo de capacidades del rol.
2. **Definí** los requerimientos y dispositivos objetivos (móvil, tablet, desktop) antes de maquetar.
3. **Implementá** componentes React o Next.js explotando características modernas (ej: `useActionState`, `useOptimistic` para formularios y Server Actions).
4. **Validá** la performance del componente analizando posibles fugas de memoria y bloqueos de renderizado.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Catálogo de capacidades, flujos de respuesta para requerimientos del usuario y listas de tecnologías soportadas en maquetado, testing, estado y optimización.

## Áreas de Maestría Cubiertas

*   **React 19 & Next.js 15:** Renderizado híbrido (Server y Client Components), hidratación progresiva, Streaming con Suspense y Server Actions para mutaciones.
*   **Arquitectura y DX:** Configuración de linters, formateadores, git hooks (Husky, lint-staged), y desarrollo orientado a componentes bajo Atomic Design.
*   **Optimización de Core Web Vitals:** Minimización del Cumulative Layout Shift (CLS), precarga de recursos críticos, lazy-loading de imágenes y fuentes variables.

## Estructura

```
frontend-developer/
└── SKILL.md                  # Pautas generales del rol de frontend developer
```

## Skills Relacionadas

- **`frontend-dev-guidelines`** - Para conocer las reglas no negociables de arquitectura y Suspense-first locales.
- **`senior-frontend`** - Para andamios de apps y optimizaciones avanzadas de bundles.
- **`react-best-practices`** - Para optimizaciones de renderizado y cascadas de peticiones.
