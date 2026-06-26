# React State Management

Guía exhaustiva para la gestión de estado moderna en React, cubriendo desde estado local hasta stores globales y sincronización del estado del servidor.

## Resumen

Esta habilidad proporciona patrones, criterios de selección y mejores prácticas para estructurar el flujo de datos en aplicaciones de React. Incluye guías detalladas para trabajar con **Redux Toolkit**, **Zustand**, **Jotai** y **TanStack Query (React Query)**, permitiendo a los desarrolladores elegir y aplicar la herramienta adecuada según las necesidades del proyecto.

## Inicio Rápido

Para implementar un store global simple y escalable usando **Zustand**:

```typescript
import { create } from 'zustand'
import { devtools, persist } from 'zustand/middleware'

interface AppState {
  theme: 'light' | 'dark'
  toggleTheme: () => void
}

export const useStore = create<AppState>()(
  devtools(
    persist(
      (set) => ({
        theme: 'light',
        toggleTheme: () => set((state) => ({
          theme: state.theme === 'light' ? 'dark' : 'light'
        })),
      }),
      { name: 'app-storage' }
    )
  )
)
```

## Qué Incluye

- **Zustand**: Implementación rápida, middleware (devtools, persist) y patrones de cortes (slices).
- **Redux Toolkit**: Configuración típica de store, hooks tipados y slices con `createAsyncThunk`.
- **Jotai**: Estado atómico basado en primitivas (`atom`), derivados y persistencia.
- **TanStack Query**: Manejo de estado de servidor, invalidación de queries y actualizaciones optimistas (optimistic updates).
- **Guías de Migración**: Transición de Redux tradicional (Legacy) a Redux Toolkit.

## Conceptos Clave

- **Categorización del Estado**: Separación estricta entre estado local (componente), global (UI compartida), servidor (caché y datos remotos) y URL (rutas y queries).
- **Normalización**: Aplanar estructuras complejas para evitar renderizados redundantes y simplificar las actualizaciones.
- **Selectores**: Uso de selectores selectivos en lugar de suscribir componentes a todo el store, previniendo problemas de rendimiento.
- **Colocación**: Mantener el estado lo más cerca posible de donde se utiliza antes de globalizarlo.

## Estructura de la Habilidad

```
react-state-management/
├── SKILL.md                 # Guía principal de uso e integraciones
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [react-best-practices](../react-best-practices/README.md) - Buenas prácticas generales en desarrollo de componentes de React.
- [react-patterns](../react-patterns/README.md) - Patrones de diseño avanzados para React.
- [redux-migration-rtk-zustand](../redux-migration-rtk-zustand/README.md) - Estrategias de migración específicas.
- [tanstack-query-expert](../tanstack-query-expert/README.md) - Profundización en la gestión de estado de servidor.
