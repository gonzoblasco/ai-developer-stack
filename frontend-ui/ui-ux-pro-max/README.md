# UI/UX Pro Max - Design Intelligence

Guía de referencia y base de datos de patrones interactivos para la creación y revisión de diseños visuales y de interacción en aplicaciones móviles y web.

## Resumen

Esta habilidad actúa como un motor de recomendación y base de datos con reglas para la toma de decisiones estéticas y de usabilidad. Permite generar sistemas de diseño contextuales según la industria y tipo de producto, y proporciona una lista exhaustiva de control de calidad visual (Pre-Delivery Checklist) para garantizar la consistencia, el soporte de modos oscuros y la eliminación de malas prácticas de diseño en el código frontend.

## Inicio Rápido

Para generar un sistema de diseño automático según el tipo de producto e industria:

```bash
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "fintech dashboard oklch dark-mode" --design-system -f markdown
```

## Qué Incluye

- **Categorización por Prioridades**: Matriz de impacto desde accesibilidad y tamaño táctil (Crítico) hasta visualización de datos y gráficos (Bajo).
- **Herramienta de Búsqueda CLI**: Script Python (`search.py`) para consultar 10 dominios de diseño y 9 stacks tecnológicos.
- **Lista de Verificación Prevía a la Entrega (Pre-Delivery Checklist)**:
  - **Calidad Visual**: Uso exclusivo de SVG (no usar emojis para iconos), sin desplazamientos de layout en hover, logos oficiales.
  - **Interacciones**: Transiciones suaves (150-300ms) y clase `cursor-pointer` en todo elemento accionable.
  - **Modo Claro/Oscuro**: Contraste mínimo de 4.5:1 en textos, bordes y transparencias legibles.
  - **Layout**: Diseño responsivo verificado en 375px, 768px, 1024px y 1440px sin scroll horizontal en móvil.

## Conceptos Clave

- **Evitar Emojis como Iconos**: Emplear siempre íconos vectoriales coherentes (ej. Lucide o Heroicons).
- **Diseño Responsivo Independiente del Viewport**: Ajustar el padding de los elementos fijos (como navbars flotantes) para no sobreponerse o tapar contenido dinámico.
- **Consistencia en Transiciones**: Mantener micro-interacciones estables y no alterar el tamaño físico de los contenedores en el estado hover.

## Estructura de la Habilidad

```
ui-ux-pro-max/
├── SKILL.md                 # Guía general y base de datos de prioridades
├── scripts/
│   └── search.py            # Motor de búsqueda CLI de patrones y estilos
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [ui-ux-designer](../ui-ux-designer/README.md) - Fundamentos teóricos e investigación de usuarios (UX).
- [web-design-guidelines](../web-design-guidelines/README.md) - Pautas estéticas y teoría de color.
- [tailwind-patterns](../tailwind-patterns/README.md) - Implementación de tokens bajo Tailwind CSS v4.
