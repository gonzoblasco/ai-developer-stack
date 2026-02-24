# Prompt 02: SaaS Scaffold — Login + Layout + Rutas

Usar cuando: **después del Design System**, para crear la estructura base de navegación de la app.

Este prompt está basado en el prompt original de SoporteML, generalizado para cualquier SaaS B2B.

---

## Template del prompt

```
Build the foundational structure of the app. The Design System is already in place.

## 1. Supabase Integration
- Generate the Supabase client at `src/integrations/supabase/client.ts`
- Create an `AuthContext` (or similar) that wraps the app and exposes `session`, `user`, and `loading`

## 2. Login Page (`/login`)
- Email + Password form using shadcn/ui components
- On success: redirect to `[RUTA_PRINCIPAL]` (e.g., `/inbox`)
- On error: show a clear error message below the form
- Design: centered card, use the app's Design System, no sidebar

## 3. Protected Layout
- A sidebar layout wrapping all authenticated routes
- Sidebar items: [LISTAR ITEMS, ej: "Inbox", "Analytics", "Settings"]
- At the bottom of the sidebar: user's email + "Logout" button
- Main content area: uses React Router `<Outlet />`

## 4. Routes
- `/login` → public, Login page
- `/` → redirect to `[RUTA_PRINCIPAL]`
- `[RUTA_PRINCIPAL]` → protected, uses Layout, placeholder content for now
- `[OTRAS_RUTAS]` → protected, uses Layout, placeholder content for now

## 5. Route Protection
- If a user without a session tries to access a protected route, redirect to `/login`
- If a logged-in user visits `/login`, redirect to `[RUTA_PRINCIPAL]`

## Design
Use the Design System we defined. Dark mode, sidebar should be styled with the surface color,
active route should be highlighted with the primary color. Smooth transitions on route change.
```

---

## Personalización rápida

Antes de enviar, reemplazá:

| Placeholder        | Ejemplo (SoporteML)          | Tu app                        |
| ------------------ | ---------------------------- | ----------------------------- |
| `[RUTA_PRINCIPAL]` | `/inbox`                     | `/dashboard`, `/orders`, etc. |
| `[LISTAR ITEMS]`   | "Inbox, Analytics, Settings" | Los que necesites             |
| `[OTRAS_RUTAS]`    | `/analytics`, `/settings`    | Las tuyas                     |

---

## Verificación post-prompt

- [ ] `/login` es accesible sin sesión
- [ ] Cualquier ruta protegida sin sesión redirige a `/login`
- [ ] El Logout funciona
- [ ] El Sidebar muestra el email del usuario
- [ ] El item activo del Sidebar se resalta
