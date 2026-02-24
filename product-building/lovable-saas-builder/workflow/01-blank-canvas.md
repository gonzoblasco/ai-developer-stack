# Paso 1: Blank Canvas — Empezar desde Cero

## Por qué importa

Lovable tiene memoria visual. Cuando le pedís que construya sobre un proyecto con código existente o estilos implícitos, toma decisiones de diseño inconsistentes. Empezar con una **página en blanco** te da control total desde el inicio.

> [!IMPORTANT]
> Nunca le pidas a Lovable que "construya TODO de una". Eso genera código monolítico difícil de iterar. El blank canvas es el contrato de que vamos a construir capa por capa.

## El prompt de inicio

```
Create a new blank Vite + React + TypeScript + TailwindCSS + shadcn/ui project.
Do not create any pages, components, or routes yet.
The only file I need for now is the base layout shell:
- src/App.tsx with nothing but a Router and an empty placeholder
- src/index.css with the base Tailwind directives
- tailwind.config.ts configured and ready

This is the foundation. We will build everything on top of this step by step.
```

## Qué verificar antes de continuar

Antes de pasar al Paso 2, confirmá que en el preview de Lovable:

- [ ] La app compila sin errores
- [ ] La página está en blanco (no hay contenido de ejemplo)
- [ ] El título del proyecto es correcto en el `<head>`

## Qué NO hacer

- ❌ Pedir que genere páginas en este paso
- ❌ Pedir que defina rutas
- ❌ Pedir que instale dependencias extras (se hacen en pasos siguientes)
