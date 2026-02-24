# Prompt 04: Analytics Dashboard

El patrón de analytics validado en SoporteML: **Métricas numéricas + Gráficos + Tabla Top N**.

---

## Template del prompt

```
Build the Analytics page at route /analytics.

## KPI Cards (top of page)
Show [N] metric cards in a grid:
- "[METRICA_1]": [descripción] (e.g., "Total preguntas hoy")
- "[METRICA_2]": [descripción] (e.g., "Respondidas esta semana")
- "[METRICA_3]": [descripción] (e.g., "Tasa de auto-respuesta")
Each card shows: the metric name, a big number, and a trend indicator (up/down).

## Charts
Use Recharts (already available via shadcn/ui).

Chart 1 — [TITULO_GRAFICO_1] (Pie/Donut chart):
- Data: [descripción de los datos, ej: preguntas agrupadas por categoría]
- Show legend with percentages

Chart 2 — [TITULO_GRAFICO_2] (Bar chart):
- X axis: [categoría, ej: nombre del agente]
- Y axis: [métrica, ej: preguntas respondidas]
- Show value labels on top of each bar

## Table
Title: "[TITULO_TABLA]" (e.g., "Top 5 Productos más consultados")
Columns: [COLUMNA_1], [COLUMNA_2], [COLUMNA_3]
Show exactly 5 rows.

## Data
Use realistic mock data for now.
When ready to wire up: read from Supabase tables `[TABLAS_RELEVANTES]`.
Filter by: company_id of the logged-in user.

## Design
Cards and charts should use the Design System. Dark mode friendly charts
(use CSS variables for chart colors). Smooth loading animations.
```

---

## Ejemplo relleno (SoporteML)

```
KPI cards: "Total preguntas pendientes", "Respondidas hoy", "Tasa de auto-respuesta %"

Chart 1: Pie — "Consultas por Categoría"
  (Precio, Stock, Técnico, Envío, Garantía, Otro)

Chart 2: Bar — "Rendimiento por Agente"
  (X: nombre del agente, Y: preguntas respondidas esta semana)

Table: "Top 5 Productos más consultados"
  Columns: Producto, Consultas, Última consulta

Tables: questions, products. Filter by company_id.
```

---

## Notas sobre Recharts en Lovable

- Recharts viene con shadcn/ui (`recharts` en package.json), no hay que instalarlo
- Para modo oscuro, usar los colores de la paleta del Design System como `stroke` y `fill`
- El `ResponsiveContainer` siempre debe tener `width="100%"` y un `height` fijo en px
