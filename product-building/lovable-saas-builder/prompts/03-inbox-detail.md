# Prompt 03: Inbox + Detail — La Feature Principal

El patrón **Lista + Detalle + Panel de Acción** es el corazón de la mayoría de apps de soporte, CRM, y gestión. Este prompt está extraído de SoporteML.

---

## Template del prompt

```
Build the [NOMBRE_PAGINA] page at route /[RUTA].

## Layout
Split the page into two columns:
- Left column (40%): Scrollable list of [ENTIDAD] cards
- Right column (60%): Detail panel (shown when an item is selected)

## Left Column — List
Each card shows:
- [CAMPO_PRINCIPAL] (e.g., product name, customer name)
- [CAMPO_SECUNDARIO] (e.g., buyer ID, email)
- Time elapsed since creation (e.g., "hace 2 horas")
- A badge with the [CATEGORIA] (e.g., "Precio", "Stock", "Técnico")

Cards should be visually distinct when selected (highlighted border or background).
On hover: subtle lift animation.

## Right Column — Detail
When a card is clicked:
- Show [CAMPO_TEXTO_PRINCIPAL] prominently at the top
- Below: [CAMPO_RESPUESTA_O_DETALLE] in an editable textarea
- [CAMPO_EXTRA] if applicable (e.g., AI category badge, "Requires human" warning)
- At the bottom, two buttons:
  - Primary button: "[ACCION_PRINCIPAL]" (e.g., "Publicar Respuesta")
  - Outline button: "[ACCION_SECUNDARIA]" (e.g., "Descartar")

## Empty States
- No items in list: friendly illustration + message "[MENSAJE_VACIO]"
- No item selected: centered message "Seleccioná un [ENTIDAD] para ver los detalles"

## Data
For now, use realistic mock data locally (minimum 5-8 items).
Prepare the list component to accept data fetched from Supabase table `[TABLA_SUPABASE]`.
Filter by: status = '[STATUS_FILTRO]' (e.g., 'pending').

## Design
Use the Design System. The list should feel like an email inbox (Gmail-like).
```

---

## Ejemplo relleno (SoporteML)

```
Build the Inbox page at route /inbox.

Left column: list of question cards showing product name, buyer nickname,
elapsed time, and AI category badge (Precio/Stock/Técnico/Envío/Garantía/Otro).

Right column: question text prominently, AI suggested answer in editable textarea,
"Requires human" warning banner if applicable.

Buttons: "Publicar Respuesta" (primary) and "Descartar" (outline).

Empty state: "No tenés consultas pendientes 🎉"
Mock data: 6 questions with varied categories and times.
Table: `questions`, filter: status = 'pending'.
```

---

## Personalización

| Placeholder                   | Descripción                                          |
| ----------------------------- | ---------------------------------------------------- |
| `[NOMBRE_PAGINA]`             | Nombre visible (ej: "Inbox", "Pedidos", "Tickets")   |
| `[ENTIDAD]`                   | Nombre del objeto (ej: "pregunta", "pedido")         |
| `[CAMPO_PRINCIPAL]`           | Lo más importante del card (ej: nombre del producto) |
| `[CAMPO_RESPUESTA_O_DETALLE]` | El textarea editable o campo largo                   |
| `[TABLA_SUPABASE]`            | Nombre de la tabla en Supabase                       |
| `[ACCION_PRINCIPAL]`          | El botón verde/primario                              |
