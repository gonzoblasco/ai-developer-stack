# testing-patterns

Skill enfocada en patrones de diseño de pruebas unitarias, mocking avanzado y metodologías TDD utilizando Vitest como framework principal de ejecución.

## Resumen

Esta skill ayuda a implementar estrategias de testing que validan comportamientos de software en lugar de detalles internos de implementación. Cubre el mockeo seguro de módulos, APIs de terceros, variables globales y del entorno, y promueve el uso del *Factory Pattern* para estructurar datos mockeados resilientes a cambios de esquema.

**Insight Clave:** Limpia y restaura siempre el estado de tus mocks entre pruebas (`vi.clearAllMocks()`) para evitar interdependencias de estado y asegurar que tus suites de tests sean deterministas.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la filosofía de pruebas y los patrones de mockeo básico.
2. **Consultá** la sección de *Factory Pattern* en `examples/factories.ts` para crear generadores de datos reutilizables.
3. **Revisá** la guía de malas prácticas en [references/anti-patterns.md](references/anti-patterns.md) para evitar errores comunes como mockear métodos privados o lógica interna.
4. **Implementá** pruebas de interacción con componentes React utilizando las utilidades de renderizado y configuración en `examples/render-utils.tsx` y `examples/user-interaction.test.tsx`.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas fundamentales sobre testing asertivo, TDD, mockeo de dependencias y variables globales en Vitest, y listas de anti-patrones.
- **[anti-patterns.md](references/anti-patterns.md)** - Guía ampliada sobre errores comunes de testing (testing de implementación, falta de aislamiento y acoplamiento estructural).

### Ejemplos Prácticos y Plantillas

- **[mocking.ts](examples/mocking.ts)** - Demostraciones de mockeo de módulos externos y APIs globales.
- **[factories.ts](examples/factories.ts)** - Plantillas de funciones de factoría con capacidad de sobreescritura (overrides) para modelos complejos.
- **[render-utils.tsx](examples/render-utils.tsx)** - Utilidades personalizadas para renderizar componentes en entornos de prueba.
- **[user-interaction.test.tsx](examples/user-interaction.test.tsx)** - Caso de prueba completo simulando interacciones reales del usuario (clicks, tipeo) mediante `@testing-library/user-event`.

## Estructura

```
testing-patterns/
├── SKILL.md                  # Filosofía y pautas de mockeo con Vitest
├── references/               # Guía de anti-patrones y buenas prácticas
└── examples/                 # Ejemplos prácticos y setups de testing
```

## Skills Relacionadas

- **`javascript-testing-patterns`** - Para conocer la pirámide de pruebas general y la configuración de pipelines CI/CD.
- **`clean-code`** - Para aplicar los principios F.I.R.S.T. a tus archivos de pruebas.
