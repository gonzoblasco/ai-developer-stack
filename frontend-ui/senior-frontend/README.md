# Senior Frontend

Guía de desarrollo avanzado en frontend enfocado en React, Next.js, TypeScript y Tailwind CSS, incluyendo automatización, optimización de bundles y accesibilidad.

## Resumen

Esta habilidad reúne las mejores prácticas y flujos de trabajo de arquitectura frontend para la creación de proyectos, generación consistente de componentes, análisis y optimización del tamaño de bundles, patrones de diseño avanzados en React y directrices de accesibilidad (a11y).

## Inicio Rápido

### Creación de un nuevo proyecto
Si estás inicializando un proyecto estructurado:
```bash
python scripts/frontend_scaffolder.py mi-app --template nextjs --features auth,api
```

### Generar un componente con tests y Storybook
```bash
python scripts/component_generator.py UserProfile --dir src/components/ui --with-test --with-story
```

### Analizar dependencias pesadas en el bundle
```bash
python scripts/bundle_analyzer.py /ruta/a/mi-proyecto
```

## Qué Incluye

- **Andamiaje (Scaffolding)**: Estructuración automatizada para Next.js (App Router y Server Components) o React + Vite.
- **Generador de Componentes**: Plantillas parametrizables para Componentes de Cliente (`use client`), Componentes de Servidor (`async`), Custom Hooks e integración con Storybook y Vitest/Testing Library.
- **Analizador de Bundles**: Herramienta de auditoría para detectar paquetes pesados (como `moment`, `lodash` o `axios`) y sugerir alternativas eficientes.
- **Patrones de React**: Compound Components, Custom Hooks eficientes y Render Props.
- **Optimización de Next.js**: Uso racional de Server vs Client Components, componentes de optimización de imágenes (`next/image`) y fetching paralelo o asíncrono vía `Suspense`.

## Conceptos Clave

- **Acceso mediante Teclado y ARIA**: Construir UI que garantice la accesibilidad semántica.
- **Importaciones optimizadas**: Evitar la carga completa de librerías grandes aprovechando el Tree-shaking.
- **TypeScript Genérico**: Tipado avanzado para componentes reutilizables.

## Estructura de la Habilidad

```
senior-frontend/
├── SKILL.md                 # Guía y comandos principales
├── scripts/
│   ├── frontend_scaffolder.py  # Script de inicialización de proyectos
│   ├── component_generator.py  # Script de generación de componentes
│   └── bundle_analyzer.py      # Script de auditoría de paquetes/bundles
├── references/
│   ├── react_patterns.md             # Detalles de patrones de diseño
│   ├── nextjs_optimization_guide.md  # Estrategias de performance en Next.js
│   └── frontend_best_practices.md   # Guías de testing y accesibilidad
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [react-best-practices](../react-best-practices/README.md) - Buenas prácticas en React.
- [nextjs-best-practices](../nextjs-best-practices/README.md) - Directrices de desarrollo en Next.js.
- [shadcn](../shadcn/README.md) - Librería de componentes accesibles y personalizables.
