# Prompt 06: Edge Function — Template para Crear Backend

Usar cuando necesitás que Lovable cree una Edge Function para conectar a una API externa, correr lógica con Service Role o llamar al AI Gateway.

---

## Template del prompt

````
Create a new Supabase Edge Function called `[NOMBRE-DE-LA-FUNCION]`.

## Purpose
[DESCRIPCION_EN_UNA_LINEA]
Example: "This function syncs unanswered questions from MercadoLibre API and stores them in Supabase."

## Trigger
How it will be called: [Manual desde el frontend con supabase.functions.invoke() / Cron job / Webhook externo]

## Input
[Describir el body JSON que recibe, o "no body / no input"]
Example:
```json
{
  "company_id": "uuid",
  "question_id": "string"
}
````

## Logic

Step by step:

1. [PASO_1]
2. [PASO_2]
3. [PASO_3]

Example:

1. Read the company's access token from `meli_tokens` table (using Service Role)
2. If token is expired, refresh it using the MeLi refresh endpoint and update the DB
3. Call the external API: GET/POST [URL]
4. Process the response and insert/update records in `[TABLA]`
5. Return { ok: true, count: N }

## Environment Variables needed

- SUPABASE_URL (always available)
- SUPABASE_SERVICE_ROLE_KEY (always available)
- [OTHER_VAR]: [what it's for, e.g., "MELI_APP_ID: MercadoLibre App ID"]

## Authentication

[Choose one]:

- This function is called by the frontend with the user's JWT → verify the user before operating
- This function is called by a cron/webhook → use Service Role only, no user auth needed

## Response

Success: { ok: true, [other fields] }
Error: standard error response with status 400/500

## Important patterns to use

- Always include CORS headers (see patterns/cors-headers.md)
- Use Supabase Service Role client (see patterns/supabase-service-role.md)
- [If calling AI]: Use Lovable AI Gateway (see patterns/ai-gateway-lovable.md)

````

---

## Funciones de referencia (SoporteML)

| Función | Propósito |
|---------|-----------|
| `sync-meli-questions` | Llama a MeLi API, guarda preguntas en DB, genera respuesta IA |
| `publish-meli-answer` | Publica respuesta en MeLi, actualiza status en DB |
| `meli-oauth-callback` | Maneja el redirect de OAuth, guarda tokens |
| `meli-item-proxy` | Proxy autenticado para leer datos de productos de MeLi |
| `disconnect-meli` | Borra tokens y limpia estado de conexión |

---

## Cómo llamarla desde el frontend

```typescript
// Llamada básica
const { data, error } = await supabase.functions.invoke('[NOMBRE-DE-LA-FUNCION]', {
  body: { param1: 'value1' },
});

// Llamada con autenticación del usuario (incluye JWT automáticamente)
const { data, error } = await supabase.functions.invoke('[NOMBRE-DE-LA-FUNCION]', {
  body: { question_id: selectedQuestion.id },
});
````
