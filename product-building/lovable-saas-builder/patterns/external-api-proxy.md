# Pattern: External API Proxy

**Extraído de**: `meli-item-proxy` de SoporteML.
**Uso**: Cuando el frontend necesita llamar a una API externa que requiere credenciales, pero **no podés exponer esas credenciales al navegador**. La Edge Function actúa de intermediario.

---

## El problema que resuelve

```
❌ SIN proxy:
Frontend → API externa (con API key expuesta en el navegador)

✅ CON proxy:
Frontend → Edge Function → API externa (API key segura en variables de entorno)
```

---

## El patrón

```typescript
Deno.serve(async (req) => {
  if (req.method === "OPTIONS") {
    return new Response(null, { headers: corsHeaders });
  }

  try {
    // 1. Verificar que el usuario está autenticado
    const authHeader = req.headers.get("Authorization");
    if (!authHeader) {
      return new Response(JSON.stringify({ error: "Unauthorized" }), {
        status: 401,
        headers: { ...corsHeaders, "Content-Type": "application/json" },
      });
    }

    // 2. Leer parámetros del body
    const { resource_id } = await req.json();
    if (!resource_id) {
      return new Response(JSON.stringify({ error: "resource_id required" }), {
        status: 400,
        headers: { ...corsHeaders, "Content-Type": "application/json" },
      });
    }

    // 3. Verificar usuario y obtener sus credenciales de la DB
    //    (ver patterns/auth-verification.md)
    const supabase = createClient(SUPABASE_URL, SUPABASE_SERVICE_ROLE_KEY);
    // ... verificar user y obtener company's access_token ...

    // 4. Llamar a la API externa con las credenciales de la empresa
    const externalHeaders: Record<string, string> = {};
    if (accessToken) {
      externalHeaders.Authorization = `Bearer ${accessToken}`;
    }

    const [primaryRes, secondaryRes] = await Promise.all([
      fetch(`https://api.external-service.com/resource/${resource_id}`, {
        headers: externalHeaders,
      }),
      fetch(
        `https://api.external-service.com/resource/${resource_id}/details`,
        { headers: externalHeaders },
      ),
    ]);

    const primaryData = primaryRes.ok ? await primaryRes.json() : null;
    const secondaryData = secondaryRes.ok ? await secondaryRes.json() : null;

    // 5. Devolver los datos combinados al frontend
    return new Response(
      JSON.stringify({
        resource: primaryData,
        details: secondaryData,
      }),
      { headers: { ...corsHeaders, "Content-Type": "application/json" } },
    );
  } catch (error) {
    console.error("Proxy error:", error);
    return new Response(JSON.stringify({ error: error.message }), {
      status: 500,
      headers: { ...corsHeaders, "Content-Type": "application/json" },
    });
  }
});
```

## Técnica: Fallback en cascada

SoporteML usa múltiples intentos si la API externa falla:

```typescript
// Intento 1: Con autenticación
let res = await fetch(`${API_URL}/items/${id}`, { headers: authHeaders });
if (res.ok) return await res.json();

// Intento 2: Sin autenticación (endpoint público, si existe)
res = await fetch(`${API_URL}/items/${id}`);
if (res.ok) return await res.json();

// Intento 3: Endpoint alternativo (multiget, bulk, etc.)
res = await fetch(`${API_URL}/items?ids=${id}`, { headers: authHeaders });
if (res.ok) {
  /* procesar respuesta diferente */
}

return null; // Si todos fallan, devolver null
```

## Cuándo usar este patrón

- ✅ API keys o tokens de terceros que no deben exponerse
- ✅ APIs que requieren el token OAuth del usuario (guardado en Supabase)
- ✅ Combinar datos de múltiples endpoints en un solo request
- ❌ APIs públicas sin auth (el frontend puede llamarlas directamente)
