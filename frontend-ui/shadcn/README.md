# shadcn/ui

Guía de referencia para la construcción de interfaces de usuario y sistemas de diseño utilizando la CLI y los componentes de shadcn/ui.

## Resumen

Esta habilidad encapsula las mejores prácticas, reglas críticas de maquetación/composición y flujos de trabajo recomendados para interactuar con la CLI oficial de `shadcn/ui`. Permite añadir, actualizar y depurar componentes directamente en el codebase, asegurando la consistencia semántica, la accesibilidad (a11y) y el uso correcto de Tailwind CSS.

## Inicio Rápido

Para interactuar con la CLI en tu proyecto (sustituye por tu gestor de paquetes correspondiente: `npx`, `pnpm dlx`, `bunx`):

### 1. Inicializar shadcn en el proyecto
```bash
npx shadcn@latest init --preset base-nova
```

### 2. Buscar y agregar componentes
```bash
npx shadcn@latest search @shadcn -q "sidebar"
npx shadcn@latest add button card dialog
```

### 3. Obtener URLs de documentación oficial
```bash
npx shadcn@latest docs button dialog
```

## Qué Incluye

- **Reglas Críticas de Composición**: Directrices de composición correctas para elementos complejos (`Card`, `Dialog`, `Avatar`, `Tabs`, `Select`).
- **Jerarquía y Estructura de Formularios**: Patrones recomendados usando `FieldGroup` + `Field` y manejo correcto de estados inválidos (`data-invalid` / `aria-invalid`).
- **Control de Clases Condicionales**: Uso de `cn(...)` en lugar de ternarios manuales.
- **Soporte de Íconos**: Dimensionamiento automático a través de `data-icon` sin sobredimensionar clases.
- **Diferenciación de Primitivas**: Guía práctica para `asChild` (Radix) vs `render` (Base).

## Conceptos Clave

- **Reutilización y Composición**: Usar los componentes instalados en lugar de reinventar markup o escribir divs personalizados con `animate-pulse` o `border-t` (preferir `Skeleton` y `Separator`).
- **Tamaños Simétricos**: Usar `size-*` en Tailwind cuando el ancho y el alto coinciden (ej. `size-10` en vez de `w-10 h-10`).
- **Colores Semánticos**: Emplear siempre variables como `bg-background` o `text-muted-foreground` en lugar de colores planos (`bg-blue-500`) para soportar de manera nativa el modo oscuro.

## Estructura de la Habilidad

```
shadcn/
├── SKILL.md                 # Guía general e integraciones CLI
├── cli.md                   # Referencia de comandos CLI
├── customization.md         # Temas, variables CSS y extensiones de componentes
├── rules/
│   ├── styling.md           # Reglas de clases Tailwind, espaciados y dark mode
│   ├── forms.md             # Layout y validación de formularios
│   ├── composition.md       # Composición de grupos, overlays y componentes base
│   ├── icons.md             # Reglas para el uso e importación de iconos
│   └── base-vs-radix.md     # Comparativa y propiedades radix/base
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [tailwind-patterns](../tailwind-patterns/README.md) - Patrones avanzados y optimización con Tailwind CSS.
- [react-ui-patterns](../react-ui-patterns/README.md) - Patrones de carga y estados de error.
- [accessibility-audit](../accessibility-audit/README.md) - Aseguramiento de accesibilidad semántica.
