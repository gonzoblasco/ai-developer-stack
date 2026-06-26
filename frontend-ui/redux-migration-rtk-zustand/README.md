# Redux Migration: Redux → RTK → Zustand

Guía experta para la refactorización incremental de Redux clásico a Redux Toolkit (RTK), y posteriormente de RTK a Zustand.

## Resumen

Esta habilidad proporciona estrategias de migración incremental y sin riesgos (slice por slice) para modernizar el manejo del estado global en aplicaciones React. Incluye guías detalladas, scripts de detección de código heredado (legacy) y patrones para coexistir con stores antiguos durante la transición.

## Inicio Rápido

### 1. Diagnosticar estado actual
Ejecuta el script incluido para encontrar qué partes usan Redux clásico, RTK o Zustand:
```bash
./scripts/detect_redux_legacy.sh ./src
```

### 2. Migración paso a paso (Slice por Slice)
> [!CAUTION]
> **NUNCA migres todo el store de una sola vez.** Migra un slice o reducer a la vez y asegúrate de verificar su funcionamiento con tests antes de proceder al siguiente.

## Qué Incluye

- **Fase 1: Redux Clásico → Redux Toolkit**: Sustitución de `createStore` y reducers switch-case redundantes por `configureStore` y `createSlice` (reduciendo drásticamente el boilerplate).
- **Fase 2: RTK → Zustand**: Transición hacia una arquitectura sin proveedores (Providers), reduciendo el bundle size de ~11kb a ~1.2kb y simplificando el uso a través de hooks directos.
- **Estrategia de Rollback**: Patrón de "puente" (Bridge Hook) para alternar dinámicamente entre el store antiguo y el nuevo mediante variables de entorno durante la transición.
- **Scripts de Detección**: Herramienta bash para buscar imports legacy en el proyecto.

## Conceptos Clave

- **Evolución del Estado**:
  `Redux Clásico (Acciones + Reducers + Selectores en archivos separados) -> Redux Toolkit (Slices e Immer integrado) -> Zustand (Stores modulares autocontenidos sin Provider)`.
- **Estrategias de coexistencia**: Permitir que múltiples tecnologías de estado global convivan durante la migración sin causar incoherencias en el comportamiento de la UI.

## Estructura de la Habilidad

```
redux-migration-rtk-zustand/
├── SKILL.md                 # Guía y restricciones del proceso de migración
├── scripts/
│   └── detect_redux_legacy.sh  # Script de diagnóstico para el codebase
├── references/
│   ├── rtk-migration.md     # Detalle de la fase Redux -> RTK
│   ├── zustand-migration.md # Detalle de la fase RTK -> Zustand
│   └── detection-patterns.md# Comandos grep y patrones de detección
├── examples/
│   ├── EJEMPLO_USO.md       # Escenarios de ejecución paso a paso
│   └── real-world-migration.md # Caso de estudio de migración en e-commerce
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [react-state-management](../react-state-management/README.md) - Guía general de soluciones de estado en React.
- [react-best-practices](../react-best-practices/README.md) - Buenas prácticas de desarrollo con React.
- [clean-code](../../languages-standards/clean-code/README.md) - Principios de refactorización y legibilidad de código.
