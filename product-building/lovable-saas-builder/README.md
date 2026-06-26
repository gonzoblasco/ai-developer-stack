# Lovable SaaS Builder

Guía de arquitectura y flujos de trabajo para construir MVPs y SaaS robustos utilizando Lovable Cloud integrado con Supabase como backend completo.

## Resumen

Esta habilidad proporciona una metodología estructurada en 6 pasos para transformar ideas de producto en MVPs funcionales. Define directrices desde la creación del Design System inicial, modelado de bases de datos PostgreSQL en Supabase (con RLS), andamiaje de autenticación y layouts, hasta la conexión de APIs externas a través de Edge Functions (Deno).

## Inicio Rápido

Para iniciar el desarrollo de un SaaS o MVP en Lovable Cloud:

1. **Establecer el Lienzo en Blanco (Blank Canvas)**: Define el alcance del MVP en base al flujo inicial en `workflow/01-blank-canvas.md`.
2. **Definir el Design System**: **Nunca saltes este paso.** Configura las variables globales en `src/index.css` y `tailwind.config.ts` antes de que Lovable genere vistas para prevenir inconsistencias visuales.
3. **Estructura del prompt**: Redacta prompts enfocados a Lovable pidiendo modificaciones de código precisas e incrementales en lugar de mega-prompts complejos.

## Qué Incluye

- **Flujo de Trabajo en 6 Pasos**:
  1. Blank Canvas (Definición).
  2. Design System (Estética e identidad de marca).
  3. DB Schema (Tablas de Supabase, claves y RLS).
  4. Auth + Layout (Registro, inicio de sesión y layouts de dashboard).
  5. Feature Building (Creación incremental de características).
  6. Edge Functions (Integraciones externas y lógica de negocio).
- **Stack de Referencia Validado**: Frontend con Vite/React/Tailwind, Base de datos y Auth con Supabase, Backend con Edge Functions de Deno, y AI Gateway integrado.
- **Lista de Reglas de Lovable**: Evitar pedirle a Lovable borrar código (pedir reemplazar), y confirmación obligatoria previa a modificar Edge Functions.

## Conceptos Clave

- **Un solo feature a la vez**: Evitar que Lovable genere código inconsistente o sobrescriba lógicas correctas al forzar múltiples cambios simultáneos.
- **Row Level Security (RLS)**: Configurar políticas de acceso correctas en Supabase para proteger los datos de los usuarios en entornos multi-tenant.

## Estructura de la Habilidad

```
lovable-saas-builder/
├── SKILL.md                 # Guía general del flujo y stack de Lovable
├── workflow/                # Guías paso a paso de cada fase de desarrollo
├── prompts/                 # Ejemplos y plantillas de prompts optimizados para la IA
├── references/              # Tips y estructuras del esquema de base de datos
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [micro-saas-launcher](../micro-saas-launcher/README.md) - Lanzamiento comercial y validación rápida de ideas.
- [shadcn](../../frontend-ui/shadcn/README.md) - Componentes para acelerar layouts en Lovable.
- [postgres-best-practices](../../backend-infra/postgres-best-practices/README.md) - Diseño de esquemas de bases de datos robustos.
