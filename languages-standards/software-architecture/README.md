# software-architecture

Skill enfocada en la calidad y robustez de la arquitectura de software, estilos de codificación, estructuración de archivos y estándares de separación de conceptos.

## Resumen

Esta skill proporciona reglas de estilo de código prácticas (como el patrón de retorno temprano y la descomposición de funciones), directrices para el uso preferente de librerías y APIs de terceros frente al desarrollo a medida (*Library-First*), convenciones de nombramiento específicas y pautas para aislar capas del sistema (Negocio, UI y Datos).

**Insight Clave:** Evita la creación de cajones de sastre como carpetas o archivos llamados `utils`, `helpers` o `shared`. Atraen código desorganizado y sin cohesión. En su lugar, usa siempre nombres específicos y delimitados al dominio del negocio (ej: `OrderCalculator.ts` o `UserAuthenticator.ts`).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender las reglas de estilo generales, la separación de responsabilidades y las limitaciones de tamaño de archivos.
2. **Aplicá** el patrón de retorno temprano (*Early Return*) en tus condicionales para reducir la anidación y simplificar la lectura del código.
3. **Buscá** librerías maduras en el ecosistema (como `npm`) antes de escribir de forma manual algoritmos complejos (ej: reintentos de red, validadores de formularios, colas).
4. **Evitá** invocar ORMs o consultas directas de base de datos dentro de tus controladores HTTP o componentes de UI; delega siempre la persistencia a una capa de repositorio.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas sobre formateo de código, descomposición de funciones (límite de 50 líneas por método y 200 por archivo), enfoque de uso de librerías, y separación limpia de responsabilidades.

## Principios Técnicos Clave

*   **Retorno Temprano:** Reducir la complejidad cognitiva del código resolviendo casos de fallo o condiciones borde al inicio de la función, evitando anidar múltiples bloques `if/else`.
*   **Enfoque Library-First:** Priorizar el uso de soluciones probadas en la comunidad frente al síndrome de "No Inventado Aquí" (NIH). Si la funcionalidad es genérica (ej: autenticación, manejo de fechas), se prefiere una librería instalada o un servicio SaaS/BaaS.
*   **Aislamiento de Capas:** Mantener la lógica de negocio pura separada de la capa de visualización (React/Vue) y de los controladores de entrada de red.

## Estructura

```
software-architecture/
└── SKILL.md                  # Manual de estándares y arquitectura de software
```

## Skills Relacionadas

- **`clean-code`** - Para conocer pautas minuciosas de formato, refactorización y nomenclatura de variables.
- **`nodejs-best-practices`** - Para aplicar estos principios arquitectónicos específicamente en el entorno y runtime de Node.js.
