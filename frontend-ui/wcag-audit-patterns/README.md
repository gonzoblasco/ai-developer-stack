# WCAG Audit Patterns

Guía detallada de auditoría y remediación de accesibilidad bajo los estándares WCAG 2.2 para el cumplimiento de normativas ADA, Sección 508 y certificación VPAT.

## Resumen

Esta habilidad proporciona un flujo de trabajo riguroso para auditar contenido web frente a las directrices de accesibilidad WCAG 2.2. Cubre tanto los métodos de escaneo automático como las pruebas manuales de navegación por teclado y lectores de pantalla (VoiceOver/NVDA), proporcionando soluciones técnicas específicas para resolver violaciones de código.

## Inicio Rápido

Para auditar y resolver problemas de accesibilidad:

1. **Escaneo Automático**: Corre herramientas de análisis estático y dinámico (Axe Core, Lighthouse, WAVE) para detectar problemas obvios de estructura y contraste.
2. **Verificación Manual**: Desconecta el ratón y navega por el sitio utilizando únicamente `Tab`, `Shift+Tab`, `Space`, `Enter` y `Escape`. Verifica si hay trampas de foco (focus traps) o elementos inaccesibles.
3. **Mapear y Remediar**: Asocia cada hallazgo con un criterio WCAG 2.2 específico, asigna su severidad (Crítico, Mayor, Menor) y aplica las soluciones de código adecuadas.

## Qué Incluye

- **Criterios Core de WCAG 2.2**:
  - **Perceptible**: Ratios de contraste (4.5:1 en texto normal, 3:1 en gráficos e interfaces), textos alternativos (`alt`), e independencia del color.
  - **Operable**: Navegabilidad por teclado, foco visible, orden de tabulación y tamaño de objetivos de puntero (mínimo 24x24px, preferible 44x44px).
  - **Comprensible**: Identificación de errores de formulario y vinculación programática de etiquetas (`aria-labelledby`).
  - **Robusto**: Anuncios asíncronos mediante regiones interactivas (`aria-live="polite"`).

## Conceptos Clave

- **Verificación Manual Obligatoria**: Los escáneres automáticos solo detectan alrededor del 30-40% de los problemas de accesibilidad. Las pruebas manuales con teclado y lectores de pantalla son indispensables.
- **Remediación en Código**: Resolver los problemas modificando la estructura HTML semántica en lugar de sobrecargar el DOM con etiquetas ARIA innecesarias.

## Estructura de la Habilidad

```
wcag-audit-patterns/
├── SKILL.md                 # Guía core de auditoría y mapeo WCAG 2.2
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [accessibility-audit](../accessibility-audit/README.md) - Framework de pruebas y verificación de conformidad legal.
- [ui-a11y](../ui-a11y/README.md) - Enfoque específico en componentes móviles y StyleSeed.
- [frontend-dev-guidelines](../frontend-dev-guidelines/README.md) - Estándares generales de frontend.
