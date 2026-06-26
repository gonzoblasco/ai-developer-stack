# Tailwind CSS Patterns (v4)

Guía y patrones de diseño utilizando la arquitectura CSS-first de Tailwind CSS v4, container queries nativos, y diseño basado en OKLCH.

## Resumen

Esta habilidad resume los principios de la versión v4 de Tailwind CSS. Reemplaza el clásico archivo de configuración `tailwind.config.js` por una arquitectura basada en hojas de estilo (`@theme` en CSS), promueve el uso de container queries nativas, layouts Bento asimétricos, y la normalización cromática a través del estándar OKLCH.

## Inicio Rápido

Para definir variables y tokens de diseño bajo la arquitectura CSS-first de v4:

```css
/* global.css */
@import "tailwindcss";

@theme {
  --color-primary: oklch(0.7 0.15 250);
  --color-surface: oklch(0.98 0 0);
  
  --spacing-md: 1rem;
  --font-sans: 'Inter', system-ui, sans-serif;
}
```

Uso de **Container Queries** nativas de v4 en componentes reutilizables:
```tsx
// El contenedor define su contexto, los elementos hijos responden a su ancho
<div className="@container">
  <div className="flex flex-col @md:flex-row gap-4">
    <p>Flexible según el tamaño del contenedor parent.</p>
  </div>
</div>
```

## Qué Incluye

- **Arquitectura v4**: Compilador Oxide (Rust-based) 10 veces más rápido y abandono de PostCSS para anidamiento nativo.
- **Configuración CSS-first**: Estructuración del tema directamente en el archivo CSS global.
- **Container Queries**: Diferencias de responsividad entre Viewport Breakpoints (`md:`) y Container Breakpoints (`@md:`).
- **Esquema de Colores OKLCH**: Ventajas sobre HSL y RGB para construir paletas de diseño uniformes y accesibles.
- **Lista de Anti-patrones**: Errores comunes como la interpolación dinámica de nombres de clases y el uso excesivo de `@apply`.

## Conceptos Clave

- **Container Queries vs Viewport Breakpoints**: Diseñar componentes modulares independientes de la resolución general de la pantalla.
- **Mobile-First**: Declarar clases base para móviles y aplicar modificadores de tamaño de pantalla progresivos (`sm:`, `md:`, `lg:`).
- **Tokens Semánticos**: Nombrar colores según su propósito (`--color-primary`) en vez de sus características físicas (`--blue-500`) para facilitar modos oscuros nativos (`dark:bg-zinc-900`).

## Estructura de la Habilidad

```
tailwind-patterns/
├── SKILL.md                 # Guía principal de uso de Tailwind v4
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [shadcn](../shadcn/README.md) - Integración de componentes preconstruidos con Tailwind.
- [frontend-dev-guidelines](../frontend-dev-guidelines/README.md) - Directrices de desarrollo visual y estilos globales.
- [web-design-guidelines](../web-design-guidelines/README.md) - Teoría de diseño y grids Bento.
