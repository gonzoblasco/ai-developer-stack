# mercadolibre-api

Skill especializada en la integración, autenticación, gestión y troubleshooting de la API de Mercado Libre (MELI).

## Resumen

Esta skill proporciona guías detalladas de implementación, flujos de autenticación OAuth, ejemplos prácticos de llamadas (publicar ítems, buscar productos, interactuar con preguntas/órdenes), y estrategias para manejar códigos de error críticos (401, 403, 429) de forma robusta.

**Insight Clave:** Para evitar bloqueos y optimizar la cuota de peticiones, prioriza siempre el uso de Webhooks en lugar de Polling recurrente, e implementa de manera obligatoria una estrategia de *exponential backoff* para el manejo del error de rate limit (429).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la tabla de correspondencia de necesidades y endpoints básicos.
2. **Implementá** el flujo de autenticación OAuth consultando la guía exhaustiva en [references/oauth-guide.md](references/oauth-guide.md).
3. **Explorá** ejemplos prácticos de código en Python, Node.js o Bash en [references/code-examples.md](references/code-examples.md).
4. **Validá** las credenciales en tu entorno usando la plantilla [templates/.env.example](resources/templates/.env.example) (¡nunca subas secrets a git!).
5. **Configurá** flujos automatizados de respuesta a preguntas de clientes usando la plantilla n8n en [resources/templates/n8n-webhook-responder-preguntas.json](resources/templates/n8n-webhook-responder-preguntas.json).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Estructura del flujo OAuth, troubleshooting rápido, rate limits y listado de sites por país (MLA, MLB, MLM, etc.).
- **[oauth-guide.md](references/oauth-guide.md)** - Flujo paso a paso para intercambio de tokens de autorización y refresco de tokens vencidos.
- **[code-examples.md](references/code-examples.md)** - Código base para publicar ítems, gestionar órdenes y recibir webhooks en Node.js, Python y Bash.
- **[error-handling.md](references/error-handling.md)** - Detalle exhaustivo de códigos de error y contramedidas.

### Ejemplos y Recursos

- **[publicar-producto.py](resources/examples/publicar-producto.py)** - Script en Python para autenticación y publicación de un ítem de prueba en el sandbox.
- **[autenticacion-oauth.js](resources/examples/autenticacion-oauth.js)** - Flujo de intercambio de tokens OAuth implementado en JavaScript.
- **[n8n-webhook-responder-preguntas.json](resources/templates/n8n-webhook-responder-preguntas.json)** - Plantilla de integración n8n para responder automáticamente preguntas de usuarios.
- **[.env.example](resources/templates/.env.example)** - Plantilla de variables de entorno para resguardar ID de cliente y secrets.

## Principios Técnicos Fundamentales

*   **Refresco Proactivo de Tokens:** Los access tokens de Mercado Libre duran 6 horas. La lógica del backend debe capturar errores 401, usar el `refresh_token` almacenado para obtener un nuevo token y reintentar la llamada.
*   **Seguridad Obligatoria:** Todas las URLs de redireccionamiento (Redirect URI) y URLs de Webhooks deben ser endpoints seguros HTTPS. El `client_secret` de tu aplicación nunca debe ser expuesto al frontend.
*   **Acciones de Alto Riesgo:** Solicita siempre confirmación explícita del usuario antes de ejecutar borrados masivos, pausados de publicaciones o alteraciones de stock de alta escala.

## Estructura

```
mercadolibre-api/
├── SKILL.md                  # Pautas del ecosistema MELI
├── references/               # Guías detalladas de OAuth, errores y ejemplos
├── resources/
│   ├── templates/            # Plantillas de configuración (.env, n8n)
│   └── examples/             # Scripts de prueba (Python, JS)
```

## Skills Relacionadas

- **`api-patterns`** - Para diseñar adaptadores de APIs REST robustos y manejo de rate limits.
- **`nestjs-expert`** - Para estructurar módulos de integración de Mercado Libre en aplicaciones NestJS.
