# React/Next.js Development Workflow

Framework y orquestación de fases de desarrollo de aplicaciones basadas en React y Next.js 14+ utilizando App Router, Server Components, TypeScript y Tailwind CSS.

## Resumen

Esta habilidad sirve como un mapa de ruta e instructivo para guiar al desarrollador en las fases del ciclo de vida de un proyecto frontend moderno. Define las tareas a realizar y las habilidades específicas a invocar en cada fase: desde la inicialización y andamiaje del proyecto hasta la arquitectura de componentes, persistencia de estado, consumo de datos (fetching), navegación, formularios, testing automatizado y despliegue en producción.

## Inicio Rápido

Para estructurar las fases de desarrollo de una nueva característica o aplicación:

1. **Configurar el proyecto (Fase 1)**: Inicializa el proyecto con TypeScript y Tailwind.
2. **Componentes y Estilos (Fases 2 y 3)**: Diseña la jerarquía y estilos atómicos responsivos.
3. **Flujo de Datos y Ruteo (Fases 4 y 5)**: Integra Server Components e hidratación.
4. **Verificación de Calidad (Quality Gates)**: Antes del despliegue, asegura que la compilación pase sin errores y que las pruebas manuales y automáticas estén completas.

## Qué Incluye

### Las 8 Fases del Desarrollo
- **Phase 1: Project Setup**: Andamiaje con Vite o Next.js, linters (ESLint, Prettier) y tipado.
- **Phase 2: Component Architecture**: Jerarquías, layouts, hooks reutilizables y Zustand.
- **Phase 3: Styling and Design**: Integración de Tailwind CSS v4 y tokens de diseño.
- **Phase 4: Data Fetching**: Sincronización mediante Server Components y React Query.
- **Phase 5: Routing and Navigation**: Rutas dinámicas, interceptadas y paralelas de Next.js.
- **Phase 6: Forms and Validation**: Formularios estructurados con React Hook Form y esquemas de validación Zod.
- **Phase 7: Testing**: Unitarios e integración con Vitest, y flujos de usuario (E2E) con Playwright.
- **Phase 8: Build and Deployment**: Compilaciones de producción y despliegue en Vercel.

## Conceptos Clave

- **Uso de Server Components**: Mantener el renderizado en el servidor por defecto y utilizar `"use client"` únicamente en las hojas del árbol donde sea necesario capturar interacciones de usuario o utilizar estados de React.
- **Puertas de Control de Calidad**: Criterios indispensables para la liberación (código limpio, responsive validado, conformidad WCAG e indexación lógica).

## Estructura de la Habilidad

```
react-nextjs-development/
├── SKILL.md                 # Guía y prompts estructurados por fases de desarrollo
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [nextjs-best-practices](../../frontend-ui/nextjs-best-practices/README.md) - Buenas prácticas y patrones en Next.js.
- [senior-frontend](../../frontend-ui/senior-frontend/README.md) - Generación de componentes y optimización de bundles.
- [tailwind-patterns](../../frontend-ui/tailwind-patterns/README.md) - Estilos responsivos y layouts Bento.
