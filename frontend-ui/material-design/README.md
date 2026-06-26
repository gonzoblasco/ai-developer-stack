# material-design

Skill de referencia para la implementación del sistema de diseño Material Design (especialmente Material Design 3) de Google de forma consistente en plataformas Web, iOS (SwiftUI), Android (Jetpack Compose), React Native y Flutter.

## Resumen

Esta skill forma parte de las directrices estéticas de `design-it`. Enseña los principios fundamentales del diseño Material (elevación en el eje Z mediante sombras físicas apiladas, movimiento con propósito y retícula base de 8dp) y proporciona plantillas de código listas para usar en múltiples tecnologías.

**Insight Clave:** Material Design se inspira en el papel y la tinta digital. Las elevaciones de componentes y tarjetas no son bordes arbitrarios; indican jerarquía mediante sombras realistas. Las curvas de animación deben usar las curvas de aceleración estándar de Material (`cubic-bezier(0.4, 0.0, 0.2, 1)`).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender los conceptos core de elevación, movimiento responsivo y anatomía de componentes (FAB, Cards).
2. **Implementá** tarjetas y componentes utilizando las clases semánticas de color (primary, secondary, surface, error).
3. **Usá** las curvas de aceleración y tiempos de transición característicos de Material (ej: 280ms de transición).
4. **Validá** las sombras simulando múltiples niveles de elevación superpuestos en tus contenedores.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - ADN visual del estilo Material Design 3, reglas del grid de 8dp, tipo de letra Roboto/Google Sans, y ejemplos prácticos de tarjetas y Floating Action Buttons (FAB) en SwiftUI, Flutter (nativo), React Native (usando `react-native-paper`) y Jetpack Compose.

## Directrices Clave de Material

*   **Elevación en Z:** Los elementos proyectan sombras difusas proporcionales a su distancia sobre el plano de fondo para indicar interactividad.
*   **Movimiento Fluido:** Animaciones continuas que guían el foco del usuario (ripple effects, shared element transitions).
*   **8dp Grid System:** Todas las dimensiones y espaciados de componentes deben ser múltiplos de 8dp (o 4dp en casos excepcionales) para asegurar la uniformidad espacial.

## Estructura

```
material-design/
└── SKILL.md                  # Pautas de maquetación de Material Design
```

## Skills Relacionadas

- **`design-it`** - Skill padre para la selección de directrices y estéticas visuales.
- **`tailwind-patterns`** - Para implementar Material You utilizando clases de Tailwind personalizadas.
