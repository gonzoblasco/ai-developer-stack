# Pattern: Auth Verification — Verificar el Usuario en Edge Functions

**Extraído de**: `meli-item-proxy`, `publish-meli-answer` de SoporteML.
**Uso**: Cuando la Edge Function opera sobre datos del usuario autenticado y necesita saber quién la llama.

---

## El patrón completo

```typescript
// 1. El frontend envía el JWT en el Authorization header automáticamente
//    cuando se usa supabase.functions.invoke()

// 2. En la Edge Function, verificar el JWT:
const authHeader = req.headers.get("Authorization");
if (!authHeader) {
  return new Response(JSON.stringify({ error: "Unauthorized" }), {
    status: 401,
    headers: { ...corsHeaders, "Content-Type": "application/json" },
  });
}

const SUPABASE_URL = Deno.env.get("SUPABASE_URL")!;
const SUPABASE_ANON_KEY = Deno.env.get("SUPABASE_ANON_KEY")!;

// 3. Crear un cliente que opera como el usuario
const userClient = createClient(SUPABASE_URL, SUPABASE_ANON_KEY, {
  global: { headers: { Authorization: authHeader } },
});

// 4. Obtener el usuario verificado
const {
  data: { user },
  error: authErr,
} = await userClient.auth.getUser();
if (authErr || !user) {
  return new Response(JSON.stringify({ error: "Unauthorized" }), {
    status: 401,
    headers: { ...corsHeaders, "Content-Type": "application/json" },
  });
}

// 5. Ahora tenés el user.id verificado
// Obtener el company_id del usuario desde la tabla profiles
const adminSupabase = createClient(
  SUPABASE_URL,
  Deno.env.get("SUPABASE_SERVICE_ROLE_KEY")!,
);
const { data: profile } = await adminSupabase
  .from("profiles")
  .select("company_id")
  .eq("id", user.id)
  .single();

if (!profile?.company_id) {
  return new Response(JSON.stringify({ error: "No company associated" }), {
    status: 403,
    headers: { ...corsHeaders, "Content-Type": "application/json" },
  });
}

// A partir de acá: tenés user.id y profile.company_id seguros
```

## Variante simplificada (solo extraer user_id del token)

Cuando no necesitás hacer queries al DB para validar:

```typescript
// Extraer sub (user_id) del JWT sin verificar (solo para logging)
const authHeader = req.headers.get("Authorization");
let callerUserId: string | null = null;
if (authHeader?.startsWith("Bearer ")) {
  try {
    const anonClient = createClient(SUPABASE_URL, SUPABASE_ANON_KEY, {
      global: { headers: { Authorization: authHeader } },
    });
    const token = authHeader.replace("Bearer ", "");
    const { data: claimsData } = await anonClient.auth.getClaims(token);
    if (claimsData?.claims?.sub) {
      callerUserId = claimsData.claims.sub;
    }
  } catch (e) {
    console.warn("Could not extract user from auth header:", e);
  }
}
```

## Cuándo omitir la verificación

- ✅ Siempre verificar si la función lee o escribe datos del usuario
- 🔄 Opcional si la función es llamada por un webhook externo (ej: callback de OAuth)
- ❌ No verificar en funciones cron (no hay usuario que las llame)
