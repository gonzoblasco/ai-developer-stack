# UI Review (Next.js + Tailwind)

Guía y flujos de revisión de código enfocado en detectar errores comunes de diseño, accesibilidad (a11y), y rendimiento en proyectos que utilicen Next.js App Router y Tailwind CSS.

## Resumen

Esta habilidad permite estructurar una revisión exhaustiva de cambios en la interfaz de usuario. Evalúa la arquitectura de componentes (Server vs. Client Components), el uso de recursos optimizados (`next/image`, `next/link`), la responsividad móvil y la legibilidad de clases Tailwind CSS, proporcionando como salida un reporte ordenado por niveles de severidad (P0, P1, P2) y un plan de solución localizado.

## Inicio Rápido

Para llevar a cabo una revisión de interfaz en una ruta o componente específico (por ejemplo, `/dashboard` o `components/Navbar.tsx`):

1. **Analizar la arquitectura**: Verifica que los componentes del servidor (Server Components) sean el estándar y el uso de `"use client"` esté acotado a las hojas del árbol de componentes.
2. **Revisar clases y responsividad**: Inspecciona el uso de prefijos móviles en Tailwind CSS (`md:`, `lg:`) para evitar roturas de layout en móviles.
3. **Evaluar accesibilidad**: Confirma la presencia de estados de foco visibles (`focus-visible:ring`), etiquetas semánticas y jerarquía de encabezados (`h1` -> `h2`).

## Qué Incluye

- **Dimensiones de la Revisión**:
  - **Next.js App Router**: Verificación de Server Components, hidratación y precarga asíncrona de datos.
  - **Mantenimiento en Tailwind CSS**: Prevención del "Class Soup" (sopa de clases redundantes) y desincentivo del uso de valores arbitrarios inline o directivas `@apply` excesivas.
  - **Calidad de Accesibilidad (A11y)**: Control de landmarks semánticos, contrastes lógicos y descripciones alt.
- **Estructuración de Reporte QA**: Formato de reporte priorizado (P0 para roturas graves e hidratación, P1 para usabilidad/a11y, P2 para limpieza del código y buenas prácticas).

## Conceptos Clave

- **Foco localizado**: No proponer reestructuraciones masivas del codebase; enfocarse en cambios específicos, mínimos e incrementales.
- **Evitar antipatrones**: No ocultar errores de hidratación y no delegar la limpieza estática a directivas `@apply` si se puede encapsular en un subcomponente reutilizable de React.

## Estructura de la Habilidad

```
ui-review-nextjs-tailwind/
├── SKILL.md                 # Guía de evaluación y reporte de auditoría UI
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [nextjs-best-practices](../nextjs-best-practices/README.md) - Guías sobre App Router y SSR.
- [tailwind-patterns](../tailwind-patterns/README.md) - Buenas prácticas del compilador v4 y container queries.
- [ui-a11y](../ui-a11y/README.md) - Auditorías específicas de conformidad WCAG.
