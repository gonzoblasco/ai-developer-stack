# design-it

El enrutador y catálogo principal de estilos visuales sofisticados para interfaces de usuario, que mapea requerimientos de diseño a 48 estéticas específicas y provee 10 paletas cromáticas universales premium.

## Resumen

Esta skill actúa como el portal principal para evitar interfaces genéricas ("AI slop") al desarrollar frontend. Proporciona reglas de distribución cromática (regla 60-30-10) y clasifica 48 estilos de diseño organizados por categorías (Moderno, Profundidad/3D, Tipografía, Retro, Tendencias, Futurista y Datos).

**Insight Clave:** No inventes degradados ni uses colores de utilidad por defecto. Si el usuario no define colores, selecciona estrictamente una de las 10 paletas universales premiadas en la skill y aplica la proporción del 60% para fondos, 30% para texto/acentos y 10% para llamados a la acción (CTAs).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para conocer las paletas universales, códigos hexadecimales exactos y la matriz de 48 estilos.
2. **Identificá** la estética deseada por el usuario (ej: "Apple/VisionOS" se asocia a `spatial-design` o `glassmorphism`).
3. **Leé** el archivo `SKILL.md` específico de la sub-skill elegida en el catálogo antes de escribir el código CSS/Tailwind.
4. **Declará** las variables de color CSS/Tailwind basándote en la paleta seleccionada en el archivo de variables global del proyecto.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Catálogo de estilos, listado de códigos de colores hexadecimales (Yacht Club, Desert Mirage, Earth-Grounded, Midnight Luxury, Modern Editorial, etc.), y reglas de implementación multiplataforma.

## Las 10 Paletas Cromáticas Universales

*   **Yacht Club (Clásico):** `#F9F6F0` (Fondo), `#1B2A49` (Acento), `#C85A32` (CTA).
*   **Desert Mirage (Cálido/Orgánico):** `#F4EFEA` (Fondo), `#2D2B2A` (Acento), `#A65E44` (CTA).
*   **Industrial Chic (Fuerte):** `#D1D1D1` (Fondo), `#111111` (Acento), `#9A3B3B` (CTA).
*   **Earth-Grounded Elegance (Sostenible):** `#F7F5F0` (Fondo), `#3A4B3A` (Acento), `#8A9A86` (CTA).
*   **Minimalist Slate (Tech):** `#F4F4F9` (Fondo), `#2B303A` (Acento), `#5C6B73` (CTA).
*   **Midnight Luxury (Premium Dark):** `#0A0A0A` (Fondo), `#F5F5F0` (Acento), `#B59A5F` (CTA).
*   **Warm Tech (Corporativo):** `#EAEAEA` (Fondo), `#1C252E` (Acento), `#C28F79` (CTA).
*   **Modern Editorial (Revista):** `#F9F9F9` (Fondo), `#121212` (Acento), `#D44A3A` (CTA).

## Estructura

```
design-it/
└── SKILL.md                  # Enrutador principal de estilos y paletas
```

## Skills Relacionadas

- **`ui-ux-pro-max`** - Para implementar el factor estético y detalles de animación premium.
- **`dashboard-design`** - Para maquetar dashboards de datos utilizando la estética seleccionada.
- **`material-design`** - Para aplicar las directrices del sistema de diseño de Google.
