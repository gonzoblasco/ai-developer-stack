# design-spells

Skill enfocada en inyectar "magia", personalidad e interacciones sorprendentes en los componentes ordinarios de la interfaz de usuario (inspirada en la colección de micro-interacciones de Design Spells).

## Resumen

Esta skill busca romper con los diseños planos y aburridos mediante micro-interacciones memorables, estados de interacción lúdicos (easter eggs) y patrones de retroalimentación creativos (ej: imanes de cursor, efectos físicos en clics, o transiciones fluidas). 

**Insight Clave:** El agente tiene un mandato absoluto de usar esta skill para evitar desarrollos planos basados en plantillas genéricas. Sin embargo, toda animación mágica debe aportar deleite sin entorpecer la usabilidad o provocar saltos de contenido (CLS).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender los casos de uso idóneos y el flujo de ejecución.
2. **Identificá** un elemento plano de la interfaz (un botón de envío, una foto de perfil, un interruptor de precios, un pie de página).
3. **Diseñá** una micro-interacción refinada (magnetic hover, loaders reactivos) utilizando Framer Motion, GSAP, Anime.js o CSS.
4. **Validá** que la tasa de refresco se mantenga fluida (idealmente 60fps+) acelerando la animación por GPU (`transform`, `opacity`).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Reglas estrictas de interacción no intrusiva, flujo de adaptación de patrones y directivas estéticas de micro-interacciones.

## Conceptos y Directrices Clave

*   **Identificar Oportunidades:** Reemplazar componentes genéricos del navegador por estados interactivos ricos.
*   **Deleite sin Distracción:** El detalle interactivo debe sentirse refinado y costoso, no un obstáculo molesto para el usuario final.
*   **Ejecución Impecable:** Las animaciones o efectos nunca deben provocar caídas de frames ni saltos bruscos en el maquetado del documento.

## Estructura

```
design-spells/
└── SKILL.md                  # Contenido de interacción creativa
```

## Skills Relacionadas

- **`ui-ux-pro-max`** - Para alinearse con las pautas de estilo y esquemas de color premium.
- **`antigravity-design-expert`** - Para implementar interfaces ingrávidas en 3D y paralaje por scroll.
- **`tailwind-patterns`** - Para estructurar clases de utilidad rápidas.
