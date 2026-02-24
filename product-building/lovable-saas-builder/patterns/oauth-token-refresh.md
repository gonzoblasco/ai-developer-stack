# Pattern: OAuth Token Refresh

**Extraído de**: `sync-meli-questions`, `publish-meli-answer` de SoporteML.
**Uso**: Cuando la app guarda tokens OAuth de servicios externos (MercadoLibre, TiendaNube, etc.) y necesita renovarlos automáticamente antes de cada operación.

---

## El patrón genérico

```typescript
async function refreshTokenIfNeeded(
  supabase: any,
  tokenRow: any, // Fila de la tabla de tokens con access_token, refresh_token, expires_at
  clientId: string, // App ID del servicio externo
  clientSecret: string, // Secret del servicio externo
  tokenEndpoint: string, // URL del endpoint de refresh del servicio
): Promise<string> {
  const now = new Date();
  const expiresAt = new Date(tokenRow.expires_at);

  // Si el token expira en más de 10 minutos, usarlo directamente
  if (expiresAt.getTime() - now.getTime() > 10 * 60 * 1000) {
    return tokenRow.access_token;
  }

  if (!tokenRow.refresh_token) {
    throw new Error("Token expired and no refresh_token. User must reconnect.");
  }

  console.log("Refreshing token for company:", tokenRow.company_id);

  const res = await fetch(tokenEndpoint, {
    method: "POST",
    headers: {
      "Content-Type": "application/x-www-form-urlencoded",
      Accept: "application/json",
    },
    body: new URLSearchParams({
      grant_type: "refresh_token",
      client_id: clientId,
      client_secret: clientSecret,
      refresh_token: tokenRow.refresh_token,
    }),
  });

  if (!res.ok) {
    const errText = await res.text();
    console.error("Token refresh failed:", errText);
    throw new Error(`Token refresh failed: ${res.status}`);
  }

  const data = await res.json();
  const expiresAtNew = new Date(
    Date.now() + data.expires_in * 1000,
  ).toISOString();

  // Actualizar el token en la base de datos
  await supabase
    .from("service_tokens") // o meli_tokens, tiendanube_tokens, etc.
    .update({
      access_token: data.access_token,
      refresh_token: data.refresh_token ?? tokenRow.refresh_token,
      expires_at: expiresAtNew,
      updated_at: new Date().toISOString(),
    })
    .eq("id", tokenRow.id);

  return data.access_token;
}
```

## Uso

```typescript
// Obtener el token de la DB
const { data: tokenRow } = await supabase
  .from("service_tokens")
  .select("*")
  .eq("company_id", companyId)
  .eq("service", "mercadolibre")
  .single();

// Siempre llamar a refreshTokenIfNeeded antes de usar el token
const accessToken = await refreshTokenIfNeeded(
  supabase,
  tokenRow,
  Deno.env.get("SERVICE_CLIENT_ID")!,
  Deno.env.get("SERVICE_CLIENT_SECRET")!,
  "https://api.service.com/oauth/token",
);

// Ahora usar accessToken con la API externa
const res = await fetch("https://api.service.com/resource", {
  headers: { Authorization: `Bearer ${accessToken}` },
});
```

## Endpoints de refresh por servicio

| Servicio     | Token Endpoint                                          |
| ------------ | ------------------------------------------------------- |
| MercadoLibre | `https://api.mercadolibre.com/oauth/token`              |
| TiendaNube   | `https://www.tiendanube.com/apps/authorize/token`       |
| Shopify      | `https://{shop}.myshopify.com/admin/oauth/access_token` |

## Por qué 10 minutos de margen

Esto evita race conditions donde el token expira exactamente mientras se está usando. 10 minutos es conservador; algunos servicios recomiendan menos.
