# Prompt 05: Settings — Configuración de la Empresa

La página de Settings es donde el admin de la empresa configura la app. En SoporteML: tono de IA, auto-respuesta, reglas de exclusión, conexión con MercadoLibre, etc.

---

## Template del prompt

```
Build the Settings page at route /settings.

## Layout
Use a tab-based layout with these sections:
- "[TAB_1]": [descripción, ej: "Configuración de IA"]
- "[TAB_2]": [descripción, ej: "Integraciones"]
- "[TAB_3]": [descripción, ej: "Equipo"]

## Tab 1 — [TAB_1]
[CAMPOS_TAB_1]
Example:
- Dropdown: "Tono de respuesta IA" (Profesional / Casual / Técnico)
- Toggle: "Auto-respuesta habilitada"
- Textarea: "Instrucciones adicionales para la IA" (max 500 chars, char counter)
- Textarea: "Reglas de exclusión" (preguntas que no se responden automáticamente)
- Save button: saves to Supabase table `company_settings`, field `company_id`

## Tab 2 — [TAB_2]
[CAMPOS_TAB_2]
Example:
- Connection status card for [SERVICE]
  - If connected: show connected account + disconnect button
  - If not connected: show "Conectar [SERVICE]" button (triggers OAuth flow)

## Tab 3 — [TAB_3]
[CAMPOS_TAB_3]
Example:
- List of team members with name, email, role
- Invite by email form (for future implementation, show as disabled/coming soon)

## Data
For tabs 1 and 2: read/write from `company_settings` and `[OTHER_TABLES]`
Filter by: company_id of the logged-in user (from their profile).
For now, use mock data where Supabase is not yet connected.

## Design
Form inputs should use shadcn/ui components (Select, Switch, Textarea, Button).
Each tab should show a success toast after saving.
```

---

## Ejemplo relleno (SoporteML)

```
TAB_1 — "Configuración de IA":
  - Dropdown: tono (Profesional/Casual/Técnico) → company_settings.ai_tone
  - Toggle: auto-respuesta → company_settings.auto_reply_enabled
  - Textarea: instrucciones adicionales (500 chars) → company_settings.ai_custom_instructions
  - Textarea: reglas de exclusión → company_settings.auto_reply_exclusion_rules

TAB_2 — "Integraciones":
  - Card de MercadoLibre: si hay token en meli_tokens, mostrar "Conectado".
    Botón "Desconectar" llama a Edge Function `disconnect-meli`.
    Si no hay token, botón "Conectar MercadoLibre" lanza el OAuth flow.

TAB_3 — "Equipo":
  - Lista de profiles donde company_id = user.company_id
  - Columnas: nombre, email, rol
```
