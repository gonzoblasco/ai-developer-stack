# Pattern: Supabase Service Role Client

**Extraído de**: Todas las Edge Functions de SoporteML.
**Uso**: Cuando la Edge Function necesita hacer operaciones que omiten RLS (admin operations).

---

## El patrón

```typescript
import { createClient } from "https://esm.sh/@supabase/supabase-js@2";

// Dentro de Deno.serve:
const SUPABASE_URL = Deno.env.get("SUPABASE_URL")!;
const SUPABASE_SERVICE_ROLE_KEY = Deno.env.get("SUPABASE_SERVICE_ROLE_KEY")!;

const supabase = createClient(SUPABASE_URL, SUPABASE_SERVICE_ROLE_KEY);
```

## Cuándo usar Service Role

| Operación                                    | ¿Necesita Service Role?              |
| -------------------------------------------- | ------------------------------------ |
| Leer datos de cualquier empresa (bypass RLS) | ✅ Sí                                |
| Escribir datos omitiendo validaciones de RLS | ✅ Sí                                |
| Leer tokens de terceros (OAuth) de la DB     | ✅ Sí                                |
| Leer datos del propio usuario autenticado    | ❌ No (usar verificación de usuario) |

## Importante

> [!IMPORTANT]
> El `SUPABASE_SERVICE_ROLE_KEY` tiene acceso total a la base de datos, sin restricciones de RLS. **Nunca exponerlo al frontend**. Solo usarlo en Edge Functions (servidor).

Este cliente siempre está disponible en Lovable Cloud — no hay que configurar nada extra.

## Comparación: Service Role vs Anon Key

```typescript
// SERVICE ROLE: acceso admin completo, omite RLS
const adminSupabase = createClient(SUPABASE_URL, SUPABASE_SERVICE_ROLE_KEY);

// ANON KEY + JWT: opera como el usuario autenticado, respeta RLS
const userSupabase = createClient(
  SUPABASE_URL,
  Deno.env.get("SUPABASE_ANON_KEY")!,
  {
    global: { headers: { Authorization: req.headers.get("Authorization")! } },
  },
);
```
