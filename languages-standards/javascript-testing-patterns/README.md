# javascript-testing-patterns

Skill de referencia para la implementación de estrategias y patrones de testing robustos en aplicaciones JavaScript y TypeScript.

## Resumen

Esta skill abarca la pirámide de pruebas (unitarias, integración y extremo a extremo), selección de frameworks (Vitest, Jest, Playwright, Cypress, Testing Library), patrones de simulación (mocking y espías), simulación de APIs con MSW, metodologías TDD y la integración de pruebas en pipelines de CI/CD (GitHub Actions).

**Insight Clave:** Evalúa siempre el comportamiento y las salidas del código, no los detalles internos de la implementación. Las pruebas que dependen de la estructura interna del código se rompen innecesariamente durante las refactorizaciones.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la selección de frameworks y la pirámide de pruebas.
2. **Consultá** la guía de ejemplos prácticos y casos avanzados en [resources/implementation-playbook.md](resources/implementation-playbook.md).
3. **Escribí** tus pruebas unitarias siguiendo el patrón **AAA (Arrange, Act, Assert)** e independizando el estado en bloques `beforeEach`.
4. **Implementá** interceptores de red realistas usando MSW (*Mock Service Worker*) en lugar de mockear clientes HTTP globales a mano.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía metodológica que cubre unit testing, mockeo de temporizadores y módulos, pruebas de bases de datos, Testing Library (React), Playwright (E2E), ciclos TDD y flujos de GitHub Actions.

## Frameworks y Herramientas Cubiertos

*   **Vitest / Jest:** Para pruebas unitarias y de integración veloces, con soporte de ESM nativo.
*   **Playwright / Cypress:** Pruebas E2E en múltiples navegadores reales con mecanismos de espera automáticos (*auto-wait*).
*   **React Testing Library:** Pruebas de componentes enfocadas en la accesibilidad (roles, etiquetas) y lo que el usuario final realmente ve en pantalla.
*   **MSW (Mock Service Worker):** Mockeo de red interceptando peticiones a nivel del navegador o entorno Node.js para simular APIs reales de forma transparente.

## Estructura

```
javascript-testing-patterns/
├── SKILL.md                  # Pautas de testing principales
└── resources/
    └── implementation-playbook.md # Playbook de implementaciones y ejemplos
```

## Skills Relacionadas

- **`testing-patterns`** - Para comprender patrones de testing genéricos y agnósticos al lenguaje.
- **`javascript-mastery`** y **`typescript-expert`** - Para escribir aserciones y tipado seguro en las pruebas de código JS/TS.
