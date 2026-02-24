---
name: lovable-saas-builder
description: Usar cuando el usuario quiera construir un SaaS o MVP usando Lovable Cloud con Supabase integrado. Guía el flujo completo desde Design System hasta Edge Functions. Keywords: lovable, saas, mvp, supabase, edge function, design system, b2b, dashboard, inbox.
---

# Lovable SaaS Builder

> Convierte ideas de producto en MVPs funcionando, usando Lovable Cloud + Supabase como stack completo.

## 🗺️ Mapa de Contenido

Lee **solo los archivos que necesites** según la fase del proyecto:

| Fase              | Archivo                                                            | Cuándo leer                                |
| ----------------- | ------------------------------------------------------------------ | ------------------------------------------ |
| 0. Inicio         | `workflow/01-blank-canvas.md`                                      | Al empezar cualquier proyecto nuevo        |
| 1. Design System  | `workflow/02-design-system.md` + `prompts/01-design-system.md`     | Siempre, antes de cualquier feature        |
| 2. Schema DB      | `workflow/03-supabase-schema.md` + `references/supabase-tables.md` | Al diseñar la base de datos                |
| 3. Auth + Layout  | `workflow/04-auth-layout.md` + `prompts/02-saas-scaffold.md`       | Al crear el scaffold inicial               |
| 4. Features       | `workflow/05-feature-building.md` + prompts específicos            | Al agregar cada feature                    |
| 5. Edge Functions | `workflow/06-edge-functions.md` + `patterns/`                      | Al conectar APIs externas o lógica backend |
| Referencia rápida | `references/`                                                      | En cualquier momento                       |

---

## ⚡ El Flujo en 6 Pasos

```
[1] Blank Canvas → [2] Design System → [3] DB Schema → [4] Auth + Layout → [5] Features → [6] Edge Functions
```

**Regla de oro**: Nunca saltear el paso 2 (Design System). Una vez que Lovable genera código sin DS propio, el caos visual es difícil de revertir.

---

## 🎯 Cuándo Usar Esta Skill

**SÍ:**

- El usuario quiere construir un SaaS, dashboard o MVP en Lovable
- Necesita guía para estructurar prompts efectivos para Lovable
- Quiere conectar la app a una API externa via Edge Function
- Necesita un schema de Supabase para un producto multi-tenant

**NO:**

- El usuario trabaja con Lovable self-hosted o un stack propio (no Lovable Cloud)
- El proyecto ya tiene código y solo necesita debuggear algo específico
- Quiere automatizaciones con n8n (usar `tools-automation/n8n-workflow-builder`)

---

## 🏗️ Stack de Referencia

Este stack está validado en producción en **SoporteML** (app real de gestión de consultas de MercadoLibre con respuestas IA):

```
Frontend:  Lovable Cloud (Vite + React + TypeScript + TailwindCSS + shadcn/ui)
Database:  Supabase (PostgreSQL + Row Level Security)
Auth:      Supabase Auth (email/password)
Backend:   Supabase Edge Functions (Deno, TypeScript)
AI:        ai.gateway.lovable.dev (acceso a Gemini, GPT-4, Claude)
Storage:   Supabase Storage (archivos, imágenes)
```

---

## ⚠️ Reglas Críticas de Lovable

> [!IMPORTANT]
> Lee `references/lovable-tips.md` antes de la primera sesión. Contiene los errores más comunes y cómo evitarlos.

1. **No pedir a Lovable que borre código** → Siempre decirle que _reemplace_ o _modifique_
2. **Un feature a la vez** → Los mega-prompts generan código inconsistente
3. **Confirmar antes de modificar Edge Functions existentes** → Son costosas de reescribir
4. **El Design System va en `src/index.css` y `tailwind.config.ts`**, no en componentes individuales
