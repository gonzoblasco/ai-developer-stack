# Refactor

Habilidad especializada en refactorizar código existente para mejorar la legibilidad, reducir duplicación y alinear el código con las convenciones del proyecto, sin alterar su comportamiento observable.

## Resumen

Esta habilidad define un proceso seguro y estructurado para realizar refactorizaciones mediante commits atómicos. Enfatiza la identificación de deuda técnica, la reducción de complejidad en componentes, la unificación del manejo de errores y la verificación estricta de tipos para evitar regresiones.

## Inicio Rápido

Para iniciar un proceso de refactorización:

1. **Analizar convenciones**: Lee las directrices del proyecto (por ejemplo, `.knowledge/conventions.md`) para asegurar consistencia.
2. **Identificar y aislar**: Busca código duplicado, funciones extensas, nombres confusos o imports muertos.
3. **Refactorizar incrementalmente**: Realiza un solo cambio por commit y asegúrate de verificar que el código sigue compilando correctamente:
   ```bash
   npm run build # o tsc --noEmit
   ```

## Qué Incluye

- **Patrones de Refactorización**:
  - Extracción de lógica repetida hacia funciones auxiliares en `/lib/utils/`.
  - Subdivisión de componentes de React que superen las 150 líneas de código.
  - Unificación del manejo de errores en Server Actions.
  - Tipado estricto (eliminación de `any` en TypeScript).
- **Esquema de Commits**: Uso de mensajes estandarizados bajo el formato `refactor: <descripción concisa del cambio>`.

## Conceptos Clave

- **Comportamiento Inalterado**: El refactor solo cambia la estructura del código, nunca el comportamiento de cara al usuario. Si surge la necesidad de cambiar la lógica, se debe consultar primero.
- **Commits Atómicos**: No mezclar la incorporación de nuevas características (features) con tareas de refactorización en el mismo commit.

## Estructura de la Habilidad

```
refactor/
├── SKILL.md                 # Proceso y reglas de refactorización
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [vibe-code-cleanup](../vibe-code-cleanup/README.md) - Limpieza estética y simplificación de código.
- [clean-code](../../languages-standards/clean-code/README.md) - Principios universales de legibilidad.
