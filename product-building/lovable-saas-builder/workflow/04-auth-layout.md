# Paso 4: Auth + Layout — El Esqueleto de la App

## El patrón estándar (validado en SoporteML)

Este es el scaffold que funciona para prácticamente cualquier SaaS B2B:

```
/login              → Página pública (email + password)
/                   → Redirect a /inbox (o la página principal) si autenticado
/[ruta-principal]   → Protegida, con Layout
/analytics          → Protegida, con Layout
/settings           → Protegida, con Layout
```

### El Layout

```
┌─────────┬──────────────────────────────────────┐
│         │  Header (opcional: breadcrumb/título) │
│ Sidebar ├──────────────────────────────────────┤
│         │                                      │
│ [Nav]   │   <Outlet /> (contenido de la ruta)  │
│         │                                      │
│ Logout  │                                      │
└─────────┴──────────────────────────────────────┘
```

## Prompt → ver `prompts/02-saas-scaffold.md`

## Detalles técnicos del Auth en Lovable Cloud

Lovable usa `@supabase/auth-helpers-react` o el cliente directo de Supabase. El flujo es:

1. Usuario ingresa email/password en `/login`
2. `supabase.auth.signInWithPassword()` → retorna sesión
3. La sesión se persiste en `localStorage` automáticamente
4. El componente de protección de rutas verifica la sesión con `supabase.auth.getSession()`
5. Si no hay sesión, redirige a `/login`

## Patrón del Protected Route

```tsx
// src/components/ProtectedRoute.tsx
const ProtectedRoute = ({ children }: { children: React.ReactNode }) => {
  const { session, loading } = useAuth(); // hook que wrappea supabase.auth

  if (loading) return <LoadingSpinner />;
  if (!session) return <Navigate to="/login" replace />;

  return <>{children}</>;
};
```

## Qué verificar

- [ ] `/login` es accesible sin sesión
- [ ] Intentar acceder a una ruta protegida sin sesión redirige a `/login`
- [ ] Después de login exitoso, redirige a la ruta principal
- [ ] El botón Logout funciona (`supabase.auth.signOut()`)
- [ ] El Sidebar muestra el nombre/email del usuario logueado

## Errores comunes

- **El Sidebar no re-renderiza al cambiar de ruta**: Asegurate de que el active state del nav usa `useLocation()` de React Router, no estado local.
- **La sesión se pierde al refrescar**: Verificar que `supabase.auth.onAuthStateChange` está configurado en el contexto global.
