# dashboard-design

Skill de referencia para el diseño e implementación de interfaces analíticas, paneles de administración (dashboards) y pantallas modulares de datos.

## Resumen

Esta skill forma parte de las directrices estéticas de `design-it`. Proporciona patrones de layouts, jerarquías visuales orientadas a métricas (KPIs), esquemas de color sobrios y guías de implementación multiplataforma (Web/CSS, SwiftUI, Flutter, React Native, Jetpack Compose) para representar datos de forma clara y escaneable.

**Insight Clave:** En un panel analítico, los datos son la decoración. Evita adornos innecesarios, utiliza retículas modulares y alinea siempre los números a la derecha en las tablas para facilitar la lectura comparativa de magnitudes.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender los principios de retícula modular, jerarquía de datos y paletas de color sobrias recomendadas.
2. **Implementá** la estructura de retícula macro (Sidebar, Header, Main Content) usando CSS Grid.
3. **Usá** tipografías monoespaciadas o con anchos de caracteres tabulares homogéneos (como `Roboto Mono` o `Inter`) para representar cifras.
4. **Verificá** la responsividad de los widgets y tarjetas utilizando layouts flexibles o rejillas adaptables.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas visuales (ADN del estilo), retícula modular y ejemplos completos de implementación de tarjetas KPI y áreas de gráficos en Web, iOS (SwiftUI), Android (Jetpack Compose), React Native y Flutter.

## Directrices de Diseño Core

*   **Retícula Modular:** Distribución basada en tarjetas o widgets funcionales independientes. Lateral a la izquierda y navegación superior por defecto.
*   **Jerarquía de Datos:** Números clave (KPIs) de gran tamaño arriba; gráficos de tendencia en el centro; tablas y listas de detalle abajo.
*   **Color Semántico:** Paletas minimalistas en tonos grises o azulados. El color verde y rojo se reserva exclusivamente para indicar tendencias positivas o negativas.

## Estructura

```
dashboard-design/
└── SKILL.md                  # Pautas de maquetación de dashboards
```

## Skills Relacionadas

- **`design-it`** - Skill padre para la selección de directrices y estéticas visuales.
- **`react-ui-patterns`** - Para implementar estados de carga, esqueletos (skeletons) y errores en los widgets.
