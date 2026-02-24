# Paso 6: Edge Functions — El Backend de Lovable Cloud

## ¿Qué son y cuándo usarlas?

Las Edge Functions de Supabase son funciones serverless escritas en **TypeScript/Deno** que corren en el borde (cerca del usuario). En el contexto de Lovable Cloud, son el **único backend disponible** y es suficiente para prácticamente cualquier SaaS.

### Cuándo SÍ necesitás una Edge Function

- Llamar a una **API externa** que requiere credenciales (MercadoLibre, TiendaNube, OpenAI, etc.)
- Hacer operaciones que usan la **Service Role Key** de Supabase (operaciones admin)
- Ejecutar lógica de negocio compleja que no debería correr en el cliente
- Hacer **refresh de tokens OAuth** de terceros
- Llamar al **AI Gateway de Lovable** (`ai.gateway.lovable.dev`)

### Cuándo NO necesitás una Edge Function

- Leer/escribir datos de Supabase con RLS (el cliente hace eso directamente)
- Autenticación (Supabase Auth lo maneja)
- Cálculos simples o filtros (hacelo en el componente React)

---

## Anatomía de una Edge Function en Lovable Cloud

```typescript
import { createClient } from "https://esm.sh/@supabase/supabase-js@2";

// 1. CORS Headers (siempre primero) → ver patterns/cors-headers.md
const corsHeaders = { ... };

// 2. Handler principal
Deno.serve(async (req) => {
  // 3. Responder a preflight OPTIONS (CORS)
  if (req.method === "OPTIONS") {
    return new Response(null, { headers: corsHeaders });
  }

  try {
    // 4. Leer variables de entorno
    const SUPABASE_URL = Deno.env.get("SUPABASE_URL")!;
    const SUPABASE_SERVICE_ROLE_KEY = Deno.env.get("SUPABASE_SERVICE_ROLE_KEY")!;

    // 5. Crear cliente Supabase (admin) → ver patterns/supabase-service-role.md
    const supabase = createClient(SUPABASE_URL, SUPABASE_SERVICE_ROLE_KEY);

    // 6. [Opcional] Verificar autenticación del usuario → ver patterns/auth-verification.md

    // 7. Tu lógica de negocio acá

    // 8. Retornar respuesta
    return new Response(JSON.stringify({ ok: true }), {
      headers: { ...corsHeaders, "Content-Type": "application/json" },
    });

  } catch (error) {
    console.error("Error:", error);
    return new Response(JSON.stringify({ error: error.message }), {
      status: 500,
      headers: { ...corsHeaders, "Content-Type": "application/json" },
    });
  }
});
```

---

## Variables de entorno disponibles

Ver `references/env-vars.md` para la lista completa.

Las principales que siempre están disponibles en Lovable Cloud:

- `SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`
- `SUPABASE_ANON_KEY`
- `LOVABLE_API_KEY` (para el AI Gateway)

---

## Prompt para crear una Edge Function → ver `prompts/06-edge-function.md`

---

## Cómo llamar una Edge Function desde el frontend

```typescript
// src/integrations/supabase/client.ts o desde cualquier componente
const { data, error } = await supabase.functions.invoke(
  "nombre-de-la-funcion",
  {
    body: { param1: value1, param2: value2 },
  },
);
```

---

## Debugging

En Lovable Cloud, los logs de las Edge Functions están disponibles en el panel de Supabase integrado. Siempre agregá `console.log()` al inicio y al final de las operaciones críticas.

Ver `references/lovable-tips.md` para los errores más comunes en Edge Functions.
