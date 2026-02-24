# Pattern: AI Gateway de Lovable

**Extraído de**: `sync-meli-questions` de SoporteML.
**Uso**: Llamar a modelos de IA (Gemini, GPT-4, Claude) desde una Edge Function usando el gateway nativo de Lovable Cloud.

---

## Por qué usar el gateway de Lovable

En Lovable Cloud, está disponible la variable de entorno `LOVABLE_API_KEY` que da acceso a `ai.gateway.lovable.dev`. Esto significa que **no necesitás contratar OpenAI, Anthropic o Google por separado** para proyectos en Lovable Cloud. El gateway multimodelo está incluido.

---

## El patrón

```typescript
async function generateWithAI(
  prompt: string,
  systemPrompt: string,
): Promise<string> {
  const LOVABLE_API_KEY = Deno.env.get("LOVABLE_API_KEY");
  if (!LOVABLE_API_KEY) {
    console.warn("LOVABLE_API_KEY not available");
    return "";
  }

  const res = await fetch(
    "https://ai.gateway.lovable.dev/v1/chat/completions",
    {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Authorization: `Bearer ${LOVABLE_API_KEY}`,
      },
      body: JSON.stringify({
        model: "google/gemini-2.5-flash", // Recomendado: rápido y económico
        messages: [
          { role: "system", content: systemPrompt },
          { role: "user", content: prompt },
        ],
        temperature: 0.7,
      }),
    },
  );

  if (!res.ok) {
    console.error("AI gateway error:", await res.text());
    return "";
  }

  const data = await res.json();
  return data.choices?.[0]?.message?.content ?? "";
}
```

## Modelos disponibles

| Modelo           | Alias en gateway             | Cuándo usar                                       |
| ---------------- | ---------------------------- | ------------------------------------------------- |
| Gemini 2.5 Flash | `google/gemini-2.5-flash`    | Respuestas rápidas, uso frecuente (↑ recomendado) |
| Gemini 2.0 Pro   | `google/gemini-2.0-pro`      | Tareas complejas de razonamiento                  |
| GPT-4o Mini      | `openai/gpt-4o-mini`         | Alternativa económica                             |
| Claude 3.5 Haiku | `anthropic/claude-3-5-haiku` | Respuestas muy rápidas                            |

## Patrón para respuesta estructurada (JSON)

SoporteML usa este patrón para que la IA devuelva siempre JSON válido:

```typescript
const systemPrompt = `Respondé SIEMPRE en JSON con este formato exacto:
{"campo1": "valor", "campo2": true, "campo3": "razón breve"}`;

const content = await generateWithAI(userPrompt, systemPrompt);

// Extraer el JSON de la respuesta (la IA a veces agrega texto antes/después)
const jsonMatch = content.match(/\{[\s\S]*\}/);
if (jsonMatch) {
  const parsed = JSON.parse(jsonMatch[0]);
  // Usar parsed.campo1, parsed.campo2, etc.
}
```

## Manejo de errores

Si `LOVABLE_API_KEY` no está disponible o el gateway falla, la función debe continuar con un fallback (no crashear). En SoporteML, si no hay respuesta IA, la pregunta se guarda igual con `ai_suggested_answer = null` y el agente la responde manualmente.
