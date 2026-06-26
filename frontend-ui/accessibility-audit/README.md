# accessibility-audit

Skill enfocada en realizar auditorías de accesibilidad web (a11y) exhaustivas bajo los estándares WCAG, navegación por teclado y compatibilidad con lectores de pantalla.

## Resumen

Esta skill proporciona pautas de inspección de barreras de acceso en interfaces de usuario. Cubre la validación de indicadores de foco claros, semántica HTML para lectores de pantalla, uso adecuado de atributos ARIA, ratios de contraste de color y flujos de pruebas manuales y automatizadas.

**Insight Clave:** La accesibilidad no es un añadido estético. Usar HTML semántico en lugar de divs genéricos con manejadores de clicks y asegurar que el orden de foco sea lógico resuelve la gran mayoría de los fallos de accesibilidad.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender las tres áreas core de auditoría (Teclado, Lectores de pantalla y Contraste).
2. **Ejecutá** una auditoría automatizada preliminar (Lighthouse, Axe o Playwright).
3. **Validá** la navegabilidad realizando un recorrido manual utilizando únicamente el teclado (`Tab`, `Shift+Tab`, `Enter`, `Space`, `Esc`).
4. **Verificá** el comportamiento dinámico con un lector de pantalla (ej: VoiceOver en macOS).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas fundamentales sobre navegación por teclado, compatibilidad con lectores de pantalla, contraste visual y flujos de testing.

## Áreas Core de Inspección

*   **Navegación por Teclado:** Evitar trampas de foco, forzar anillos de foco altamente visibles y garantizar que la secuencia de tabulación sea natural.
*   **Lectores de Pantalla:** Uso estricto de etiquetas semánticas nativas (`<main>`, `<nav>`, `<button>`) y alt text en imágenes. Atributos ARIA aplicados solo cuando el marcado nativo sea insuficiente.
*   **Contraste y Color:** Ratios de contraste mínimos de `4.5:1` para texto normal. No transmitir información de estados críticamente importantes solo con colores (ej: añadir íconos o subrayados).

## Estructura

```
accessibility-audit/
└── SKILL.md                  # Manual de auditoría de accesibilidad
```

## Skills Relacionadas

- **`wcag-audit-patterns`** - Para profundizar en listas de cumplimiento extendidas de WCAG 2.2.
- **`ui-a11y`** - Para auditoría móvil y componentes interactivos específicos.
