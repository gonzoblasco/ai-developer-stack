# antigravity-design-expert

Skill experta en diseño de movimiento e interfaces espaciales "Antigravity", especializada en crear experiencias visuales fluidas en 3D, micro-interacciones interactivas y glassmorphism usando GSAP y CSS 3D.

## Resumen

Esta skill reúne directrices avanzadas de ingeniería UX/UI enfocadas en dotar a las interfaces de ligereza, profundidad espacial y fluidez animada. Establece las bases para animaciones basadas en scroll, retículas isométricas dinámicas, efectos de desenfoque de fondo y transformaciones tridimensionales de tarjetas y layouts.

**Insight Clave:** El diseño "Antigravity" busca dar una ilusión de ingravidez. Para lograrlo, utiliza sombras difusas y de múltiples capas, perspectivas tridimensionales dinámicas al interactuar con el cursor, y transiciones suaves (`will-change: transform`) para delegar el renderizado al chip gráfico (GPU).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para familiarizarte con los principios del estilo (ingravidez, profundidad espacial, glassmorphism e isometricidad).
2. **Implementá** animaciones de entrada escalonadas (*staggers*) y efectos de paralaje utilizando GSAP y ScrollTrigger.
3. **Validá** que todas las animaciones pesadas respeten la preferencia del sistema del usuario desactivándose bajo la media consulta `prefers-reduced-motion: reduce`.
4. **Evitá** animar propiedades costosas de forma continua (como filtros de desenfoque o sombras de caja) para no provocar caídas de frames en el renderizado.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía de diseño de movimiento, especificaciones de la pila tecnológica (React/Tailwind/GSAP/R3F), y reglas de optimización de rendimiento gráfico.

## Principios del Estilo Antigravity

*   **Ingravidez y Flotación:** Tarjetas y contenedores con elevaciones visuales simuladas mediante sombras difusas muy suaves en lugar de bordes planos y pesados.
*   **Profundidad Espacial (Z-Axis):** Disposición de capas en el eje Z utilizando la propiedad CSS `perspective` para dar tridimensionalidad.
*   **Glassmorphism Estricto:** Combinación de color traslúcido, desenfoque de fondo (`backdrop-filter: blur()`) y bordes brillantes semi-transparentes que simulan vidrio templado.
*   **Perspectiva Isométrica:** Rotaciones en 3D (`rotateX(60deg) rotateZ(-45deg)`) para presentar retículas de forma isométrica e inmersiva.

## Estructura

```
antigravity-design-expert/
└── SKILL.md                  # Contenido principal de la skill
```

## Skills Relacionadas

- **`ui-ux-pro-max`** - Para pulir detalles estéticos y alineación visual premium.
- **`threejs-fundamentals`** - Para implementar escenas WebGL interactivas más complejas.
- **`tailwind-patterns`** - Para estructurar clases de utilidad rápidas sobre los layouts en 3D.
