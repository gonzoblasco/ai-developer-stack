# Prompt 01: Design System

Usar cuando: **iniciar un proyecto nuevo antes de cualquier feature**.

---

## Template del prompt

Personalizá los valores entre `[CORCHETES]` antes de enviar a Lovable.

```
Now let's establish the Design System for this app.

Apply the following design tokens to `src/index.css` (as CSS custom properties on :root)
and map them in `tailwind.config.ts` so they're available as Tailwind classes.

## Color Palette (Dark Mode)
- Background: [ej: hsl(224, 71%, 4%)]       → --background
- Surface/Card: [ej: hsl(222, 47%, 11%)]    → --card
- Primary: [ej: hsl(217, 91%, 60%)]         → --primary (brand color, botones principales)
- Primary Foreground: [ej: hsl(0, 0%, 98%)] → --primary-foreground
- Secondary: [ej: hsl(215, 28%, 17%)]       → --secondary
- Muted: [ej: hsl(215, 16%, 47%)]           → --muted
- Border: [ej: hsl(215, 28%, 17%)]          → --border
- Text primary: [ej: hsl(0, 0%, 98%)]       → --foreground
- Text muted: [ej: hsl(215, 16%, 47%)]      → --muted-foreground
- Success: [ej: hsl(142, 71%, 45%)]         → --success
- Destructive: [ej: hsl(0, 84%, 60%)]       → --destructive

## Typography
- Font: Import "[Inter|Geist|Outfit|Manrope]" from Google Fonts
- Apply as the default font family to the entire app

## Component defaults
- Default border-radius: [ej: 0.5rem = rounded-lg]
- Card border: 1px solid var(--border)
- Card background: var(--card)

## shadcn/ui
- Make sure all shadcn/ui components inherit from these CSS variables (this is their default behavior, just confirm it's working)

Do not create any pages or components yet. Just apply the Design System.
```

---

## Paletas pre-armadas (copiar y pegar)

### 🌑 Dark profesional (usado en SoporteML)

```
Background: hsl(224, 71%, 4%)
Surface: hsl(222, 47%, 11%)
Primary: hsl(217, 91%, 60%)
Border: hsl(215, 28%, 17%)
Muted: hsl(215, 16%, 47%)
```

### 🟣 Dark violeta (SaaS moderno)

```
Background: hsl(260, 30%, 5%)
Surface: hsl(260, 20%, 10%)
Primary: hsl(262, 83%, 65%)
Border: hsl(260, 20%, 18%)
Muted: hsl(260, 15%, 45%)
```

### 🟢 Dark verde (fintech / datos)

```
Background: hsl(160, 20%, 4%)
Surface: hsl(160, 15%, 9%)
Primary: hsl(142, 71%, 45%)
Border: hsl(160, 15%, 16%)
Muted: hsl(160, 10%, 45%)
```
