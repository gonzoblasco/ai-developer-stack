# UI Accessibility Audit

Habilidad especializada en auditar componentes y páginas (especialmente en entornos de diseño basados en StyleSeed y mobile UI) bajo los estándares WCAG 2.2 AA.

## Resumen

Esta habilidad proporciona una guía detallada y patrones prácticos de corrección para problemas comunes de accesibilidad (a11y) tales como tamaño de objetivos táctiles (touch targets), visibilidad del foco del teclado, contraste de colores de texto y no texto, etiquetas de lectores de pantalla, y soporte para movimiento reducido.

## Inicio Rápido

Para auditar un componente o página interactiva, enfócate en evaluar y corregir las siguientes cuatro categorías de WCAG:

### 1. Perceptibilidad (Perceivable)
Verifica que las imágenes y elementos multimedia tengan etiquetas descriptivas (`alt` o `aria-label`). Asegura que los textos pasen la prueba de ratio de contraste mínimo (WCAG AA: 4.5:1 para texto normal, 3:1 para texto grande).

### 2. Operabilidad (Operable)
Asegura que los objetivos táctiles interactivos en dispositivos móviles midan al menos **44x44px** y tengan indicadores de foco de teclado visibles (`focus-visible:ring-2`).

## Qué Incluye

- **Contraste de Texto y No-Texto**: Directrices para revisar que los bordes, íconos y textos contrasten correctamente con el fondo.
- **Reachability (Accesibilidad de Teclado)**: Aseguramiento de un orden de tabulado lógico (`tabIndex`) y de que todo control sea accionable con teclado.
- **Soporte de Movimiento Reducido**: Buenas prácticas de CSS para animaciones respetando la propiedad `prefers-reduced-motion`.
- **Estructura del Reporte**: Patrón de reporte de auditoría (Crítico, Mayor, Menor, Correcciones automáticas sugeridas, y Puntos de revisión manual).

## Conceptos Clave

- **Semántica Primero**: Usar componentes HTML semánticos (`<button>`, `<a href>`, `<nav>`) antes de recurrir a atributos ARIA redundantes.
- **Objetivos Táctiles (Touch Targets)**: Tratar los botones de menor tamaño a 44x44px como fallos de diseño de usabilidad críticos en entornos móviles.
- **No dependencia exclusiva del color**: No transmitir estados importantes (errores, éxito) únicamente mediante colores.

## Estructura de la Habilidad

```
ui-a11y/
├── SKILL.md                 # Especificaciones de la auditoría a11y StyleSeed
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [accessibility-audit](../accessibility-audit/README.md) - Plantilla general de cumplimiento legal de accesibilidad.
- [frontend-dev-guidelines](../frontend-dev-guidelines/README.md) - Pautas generales de desarrollo de interfaces.
- [ui-review-nextjs-tailwind](../ui-review-nextjs-tailwind/README.md) - Revisión estética y funcional de layouts basados en Tailwind CSS.
