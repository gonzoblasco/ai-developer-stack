---
name: security-audit
description: Realizar un análisis profundo y focalizado en la superficie de ataque del código desarrollado durante el ciclo.
risk: unknown
source: community
date_added: "2026-06-26"
---

# Skill: Security Audit (Modelo de Amenazas y Blindaje)

## Propósito

Realizar un análisis profundo y focalizado en la superficie de ataque del código desarrollado durante el ciclo. A diferencia de un linter general, este skill opera bajo el modelo de amenazas específico del backend, garantizando el aislamiento absoluto de datos (_Multi-Tenancy_) y la integridad de las llaves del sistema.

---

## Vectores Críticos de Inspección

### 1. Fugas de Datos en Multi-Tenancy (Aislamiento de Clientes)

- **El Peligro:** El uso indebido de clientes de base de datos con rol de servicio o superusuario (`service_role`, `admin_client`) salta las reglas de seguridad por fila (RLS).
- **Regla de Auditoría:** Toda consulta realizada mediante un cliente de bypass _debe_ incluir un filtro explícito de pertenencia a la empresa o inquilino en la cláusula `WHERE`.
- **Código Inválido:** `db.from('records').select('*')` ❌ (Fuga masiva potencial)
- **Código Seguro:** `db.from('records').select('*').eq('company_id', current_company)` (Aislado)

### 2. Verificación de Autenticación en Endpoints (Auth Guards)

- **Regla de Auditoría:** Todo archivo dentro de directorios de rutas de API (`/api/v1/`, `/api/routes/`) debe implementar explícitamente la verificación de la sesión activa del usuario solicitante al inicio del método, a menos que esté documentado explícitamente como un endpoint público controlado.

### 3. Validación de Secretos Internos de Comunicación

- **Regla de Auditoría:** Los endpoints diseñados para consumo exclusivo entre microservicios, middlewares internos o webhooks externos (ej: automatizaciones de n8n, triggers de colas de mensajería) deben validar obligatoriamente la presencia y exactitud de llaves secretas en las cabeceras de la petición.
- **Ejemplo:** Validación de `x-internal-secret` o `x-webhook-signature`.

### 4. Exposición de Datos Sensibles en Capas de Cliente (Frontend Leak)

- **Regla de Auditoría:** Verificar que los modelos de datos devueltos al cliente web no arrastren columnas de credenciales, tokens de refresco, Hashes de contraseñas o datos de integración crudos de plataformas de terceros. Toda serialización de datos hacia el frontend debe estar explícitamente acotada.

---

## Mecanismo de Salida y Bloqueo

Al ejecutarse (vía CLI o análisis de entorno de Antigravity), el skill genera una lista de hallazgos. Cualquier hallazgo en la categoría **Multi-Tenancy** o **Auth Guards** arroja automáticamente un estado de **FALLO CRÍTICO**, bloqueando cualquier intento de ejecución del skill `Close-Epic`.
