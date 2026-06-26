# frontend-dev-guidelines

Lineamientos y estándares arquitectónicos no negociables para el desarrollo de aplicaciones frontend a nivel de producción usando React, TypeScript y Suspense-first.

## Resumen

Esta skill define la doctrina de desarrollo para estructurar aplicaciones frontend robustas. Introduce el *Frontend Feasibility & Complexity Index (FFCI)* para medir la viabilidad de componentes, promueve la arquitectura basada en carpetas por dominio (*features*), impone el patrón asíncrono basado en `Suspense` (sin spinner intermedios manuales), la carga perezosa de elementos pesados y el tipado estricto en TypeScript.

**Insight Clave:** La carga de datos con `useSuspenseQuery` es el estándar por defecto. Quedan prohibidos los retornos tempranos condicionales como `if (isLoading) return <Spinner />`, delegando en su lugar los estados de carga y error a los límites nativos de `<Suspense>` y `<ErrorBoundary>` a nivel de contenedor.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la doctrina arquitectónica, el cálculo de FFCI y la estructura de archivos obligatoria.
2. **Calculá** el FFCI de tu propuesta antes de iniciar la codificación (se requiere FFCI ≥ 6 para continuar).
3. **Estructurá** las carpetas bajo el enfoque de dominios: `features/{nombre-feature}/` (`api/`, `components/`, `hooks/`, `types/`).
4. **Validá** tus componentes usando el checklist de control (memorización de handlers, tipado estricto y sin spinners locales).
5. **Cargá perezosamente** (`React.lazy`) cualquier ruta, gráfico, editor o modal pesado.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Estándares detallados sobre la jerarquía del ciclo de vida de peticiones, alias de importación obligatorios (`@/`, `~types`, `~features`), reglas de grids en MUI v7 y plantillas canónicas de código.

## Reglas Clave del Componente Canónico

*   **Orden de Declaración:** Props/Tipos ➔ Hooks ➔ Valores calculados (`useMemo`) ➔ Manejadores (`useCallback`) ➔ Render ➔ Export por defecto.
*   **Manejo de Red:** Prohibidas las llamadas HTTP directamente en los componentes de UI; deben estar encapsuladas en la capa de API de la *feature*.
*   **Mensajería:** Uso exclusivo del hook de sistema `useMuiSnackbar` para notificaciones visuales (toast) de cara al usuario.

## Estructura

```
frontend-dev-guidelines/
└── SKILL.md                  # Doctrina y plantilla de desarrollo frontend
```

## Skills Relacionadas

- **`senior-frontend`** - Para andamios de apps y optimizaciones avanzadas de bundles.
- **`react-best-practices`** - Para optimizaciones de renderizado y cascadas de peticiones.
- **`react-state-management`** - Para la toma de decisiones sobre sincronización de datos de servidor con TanStack Query y estado global con Zustand.
