# Environment Variables en Lovable Cloud

Variables de entorno disponibles automáticamente en toda Edge Function de Lovable Cloud.

---

## Variables automáticas (siempre disponibles)

| Variable                    | Descripción                     | Cómo obtenerla                               |
| --------------------------- | ------------------------------- | -------------------------------------------- |
| `SUPABASE_URL`              | URL del proyecto Supabase       | `Deno.env.get("SUPABASE_URL")!`              |
| `SUPABASE_SERVICE_ROLE_KEY` | Clave admin que bypasea RLS     | `Deno.env.get("SUPABASE_SERVICE_ROLE_KEY")!` |
| `SUPABASE_ANON_KEY`         | Clave pública (respeta RLS)     | `Deno.env.get("SUPABASE_ANON_KEY")!`         |
| `LOVABLE_API_KEY`           | Acceso al AI Gateway de Lovable | `Deno.env.get("LOVABLE_API_KEY")`            |

## Variables personalizadas (se agregan en Lovable Cloud)

En Lovable Cloud, se gestionan desde el panel de Supabase → Edge Functions → Secrets.

### Convención de nombres

Usar `SCREAMING_SNAKE_CASE`. Prefijo con el nombre del servicio externo:

```
MELI_APP_ID             → ID de la app de MercadoLibre
MELI_SECRET_KEY         → Secret de la app de MercadoLibre
TIENDANUBE_CLIENT_ID    → ID de la app de TiendaNube
TIENDANUBE_SECRET       → Secret de TiendaNube
OPENAI_API_KEY          → Si usás OpenAI directamente (no vía gateway)
```

## Cómo pedirle a Lovable que las configure

```
I need to add the following environment variables (secrets) to the Edge Functions:
- MELI_APP_ID = [valor]
- MELI_SECRET_KEY = [valor]

Please add them to the Supabase project secrets and use them in the [function-name] Edge Function.
```

## Acceso desde el frontend

Las variables de entorno **NO son accesibles desde el frontend**. Solo desde Edge Functions. Para exponer configuración al frontend, almacenarla en Supabase (tabla de settings) con RLS apropiado.

## Nunca hardcodear

```typescript
// ❌ MAL
const apiKey = "super-secret-key-hardcoded";

// ✅ BIEN
const apiKey = Deno.env.get("MY_API_KEY")!;
```
