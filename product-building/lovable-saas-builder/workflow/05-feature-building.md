# Paso 5: Feature Building — Agregar Funcionalidad Incrementalmente

## El principio fundamental

> **Un prompt = Una feature**

Lovable trabaja mejor cuando cada conversación tiene un objetivo claro y acotado. Los prompts largos con múltiples features generan código inconsistente y son difíciles de revertir.

---

## Cómo estructurar un buen prompt de feature

### Estructura recomendada

```
[CONTEXTO] Qué existe actualmente en la app
[OBJETIVO] Qué queremos agregar/modificar
[DATOS] Desde qué tabla de Supabase viene la data
[UI] Cómo debe verse (columnas, cards, botones, etc.)
[ACCIONES] Qué puede hacer el usuario (click, submit, delete)
[EDGE CASES] Qué pasa cuando no hay datos, hay error, etc.
```

### Ejemplo real (Inbox de SoporteML)

```
The app currently has the Layout with Sidebar and routing.
Now I need to build the Inbox page at route /inbox.

DATA: Read from Supabase table `questions` where status = 'pending'.
Filter by the user's company_id (from their profile).

UI: Split into two columns:
- Left (40%): Scrollable list of question cards. Each card shows:
  product name, buyer nickname, elapsed time since creation, and
  an AI category badge (Precio/Stock/Técnico/Envío/Garantía/Otro)
- Right (60%): Detail panel. When a card is clicked:
  - Show the full question text prominently
  - Show the AI suggested answer in an editable textarea
  - Two buttons at the bottom: "Publicar Respuesta" (primary) and "Descartar" (outline)

EMPTY STATE: If there are no pending questions, show a friendly message with an icon.

Use the Design System colors and components we defined earlier.
```

---

## Tipos de features comunes

| Feature                                    | Prompt base en                |
| ------------------------------------------ | ----------------------------- |
| Lista + Detalle (Inbox)                    | `prompts/03-inbox-detail.md`  |
| Dashboard Analytics                        | `prompts/04-analytics.md`     |
| Settings de empresa                        | `prompts/05-settings.md`      |
| Conexión con API externa via Edge Function | `prompts/06-edge-function.md` |

---

## Técnica del "Mock first"

Cuando la Edge Function aún no existe, pedile a Lovable que use datos mock primero:

```
For now, use mock data locally to make the UI complete and beautiful.
Prepare the components to fetch from Supabase later, but don't wire it up yet.
```

Esto acelera la validación visual antes de escribir backend.

---

## Cuándo hacer un nuevo chat en Lovable

Empezá un nuevo chat (contexto fresco) cuando:

- La feature anterior está completa y verificada
- Vas a cambiar algo significativo del Design System
- Vas a crear una Edge Function nueva
- El chat tiene más de ~15 mensajes (el contexto de Lovable se degrada)
