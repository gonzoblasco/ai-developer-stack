# Pattern: CORS Headers

**Extraído de**: Todas las Edge Functions de SoporteML.
**Frecuencia de uso**: SIEMPRE — en el 100% de las Edge Functions.

---

## El bloque

```typescript
const corsHeaders = {
  "Access-Control-Allow-Origin": "*",
  "Access-Control-Allow-Headers":
    "authorization, x-client-info, apikey, content-type, x-supabase-client-platform, x-supabase-client-platform-version, x-supabase-client-runtime, x-supabase-client-runtime-version",
};
```

## Cómo usarlo

```typescript
Deno.serve(async (req) => {
  // SIEMPRE responder a OPTIONS primero
  if (req.method === "OPTIONS") {
    return new Response(null, { headers: corsHeaders });
  }

  // ... tu lógica ...

  // Siempre incluir corsHeaders en TODA respuesta
  return new Response(JSON.stringify({ ok: true }), {
    headers: { ...corsHeaders, "Content-Type": "application/json" },
  });
});
```

## Por qué es necesario

El frontend de Lovable (que corre en `https://[project].lovable.app`) hace requests a las Edge Functions (que corren en `https://[project].supabase.co/functions/v1/[name]`). Dominios diferentes = CORS necesario.

Sin el handler de `OPTIONS`, el navegador bloquea la request antes de que llegue a la función.

## Reglas

- ✅ Siempre en la primera línea del archivo (antes de `Deno.serve`)
- ✅ Siempre incluir `{ ...corsHeaders }` en todas las respuestas
- ✅ Siempre el handler de OPTIONS como primer `if` dentro de `Deno.serve`
- ❌ No cambiar `Access-Control-Allow-Origin: "*"` a un dominio específico (rompe el desarrollo)
