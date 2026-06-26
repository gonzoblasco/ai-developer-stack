# security-audit

Skill enfocada en el análisis profundo de la superficie de ataque, modelado de amenazas y blindaje de código en aplicaciones backend.

## Resumen

Esta skill opera bajo un modelo de amenazas específico para backend. A diferencia de un linter convencional, audita vectores críticos de vulnerabilidad como el aislamiento de datos entre clientes (*Multi-Tenancy*), la existencia de guardas de autenticación en endpoints de API, la validación de firmas de webhooks y secretos entre microservicios, y la prevención de fugas de datos sensibles hacia el cliente.

**Insight Clave:** La seguridad es un bloqueo de producción. Cualquier consulta que use clientes de bypass de base de datos sin un filtro explícito de inquilino (`tenant_id`/`company_id`) o cualquier endpoint expuesto sin control de sesión, arrojará un **FALLO CRÍTICO** inmediato.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender los 4 vectores críticos de inspección y las reglas de bloqueo automático.
2. **Revisá** que todas tus consultas a bases de datos que utilicen credenciales administrativas o de superusuario incluyan filtros explícitos en su cláusula `WHERE`.
3. **Asegurá** tus endpoints de API implementando Auth Guards robustos antes de proceder a su integración.
4. **Verificá** que la firma o token secreto se valide correctamente en las cabeceras para webhooks externos o llamados entre servicios.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas de auditoría de seguridad y políticas de bloqueo.

## Vectores Críticos Auditados

1. **Aislamiento en Multi-Tenancy (Bypass de RLS):**
   Asegura que el uso de clientes superusuario (`admin_client`, `service_role`) no exponga información cruzada. Toda consulta debe acotarse al inquilino correspondiente de forma imperativa.
2. **Validación de Sesiones (Auth Guards):**
   Garantiza que cada ruta de API verifique la identidad del usuario solicitante, a menos que esté tipificada formalmente como pública.
3. **Secretos Internos y Firmas de Webhooks:**
   Valida que los endpoints consumidos por integraciones externas (ej: n8n, Stripe, Mercado Libre) verifiquen cabeceras secretas o firmas criptográficas (`x-webhook-signature`).
4. **Prevención de Fugas de Información (Frontend Leak):**
   Audita que las transferencias de datos al cliente no serialicen datos sensibles como hashes de contraseñas, tokens de refresco o metadatos internos de infraestructura.

## Estructura

```
security-audit/
└── SKILL.md                  # Reglas del pipeline de auditoría de seguridad
```

## Skills Relacionadas

- **`api-patterns`** - Para implementar de forma consistente formatos de respuesta de error seguros.
- **`postgres-best-practices`** - Para configurar correctamente políticas RLS (Row Level Security) a nivel de base de datos.
- **`nestjs-expert`** - Para implementar Guards e Interceptors que impidan la fuga de campos de datos.
