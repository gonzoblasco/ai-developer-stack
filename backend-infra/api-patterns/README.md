# api-patterns

Skill enfocada en la toma de decisiones, arquitectura y diseño de APIs modernas para la temporada 2025.

## Resumen

Esta skill proporciona principios de diseño y árboles de decisión para seleccionar y estructurar la comunicación cliente-servidor (REST, GraphQL, tRPC, gRPC), versionado, seguridad, paginación y rate limiting.

**Insight Clave:** No copies patrones fijos por costumbre. El diseño de una API siempre debe comenzar por responder a la pregunta fundamental: _¿Quién va a consumir esta API?_

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender el mapa de contenidos y la tabla de "Excusa vs Realidad".
2. **Consultá** la guía de estilos específica en `references/` según el tipo de API a construir.
3. **Validá** la consistencia de tus endpoints y especificaciones OpenAPI/Swagger usando el script validador:
   ```bash
   python scripts/api_validator.py <ruta_de_tu_proyecto>
   ```

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía de decisiones iniciales, checklists y anti-patrones.

### Temas en Profundidad (Referencias)

- **[api-style.md](references/api-style.md)** - Árbol de decisiones entre REST, GraphQL y tRPC.
- **[rest.md](references/rest.md)** - Nombramiento de recursos, métodos HTTP y uso correcto de status codes.
- **[response.md](references/response.md)** - Estructura de respuestas (Envelope pattern), formato de errores y paginación.
- **[graphql.md](references/graphql.md)** - Diseño de esquemas y consideraciones de seguridad para GraphQL.
- **[trpc.md](references/trpc.md)** - Integración de tRPC en monorepos TypeScript para máxima seguridad de tipos.
- **[versioning.md](references/versioning.md)** - Estrategias de versionado por URI, Headers o Query strings.
- **[auth.md](references/auth.md)** - Selección de patrones de autenticación (JWT, OAuth, Passkey, API Keys).
- **[rate-limiting.md](references/rate-limiting.md)** - Algoritmos de protección de APIs (Token bucket, Sliding window).
- **[documentation.md](references/documentation.md)** - Buenas prácticas en OpenAPI/Swagger.
- **[security-testing.md](references/security-testing.md)** - Auditoría y pruebas contra el OWASP API Top 10.

### Scripts de Validación

- **[api_validator.py](scripts/api_validator.py)** - Validador automático de endpoints de API contra las pautas de diseño del repositorio.

## Estructura

```
api-patterns/
├── SKILL.md                  # Mapa de contenidos y reglas generales
├── scripts/                  # Scripts de validación de endpoints
└── references/               # Guías detalladas por tema
```

## Skills Relacionadas

- **`database-design`** - Para estructurar y optimizar el almacenamiento detrás de la API.
- **`nestjs-expert`** - Para la implementación de APIs REST/GraphQL utilizando NestJS.
- **`security-audit`** - Para profundizar en la fortificación de endpoints.
