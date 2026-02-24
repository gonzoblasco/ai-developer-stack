# Paso 2: Design System — El Contrato Visual

## Por qué va ANTES de cualquier feature

El Design System es el sistema de tokens (colores, tipografía, espaciados, border-radius) que garantiza que todos los componentes de la app tengan coherencia visual. Si Lovable genera un componente sin DS definido, inventa sus propios estilos y el resultado es inconsistente.

> [!IMPORTANT]
> Este paso es obligatorio. No se pasa al Paso 3 sin Design System definido.

## Qué define un Design System mínimo en Lovable

1. **Paleta de colores**: Primario, secundario, fondo, superficie, texto, borde, error, éxito
2. **Tipografía**: Font family (Google Fonts), tamaños y pesos (`sm`, `base`, `lg`, `xl`, `2xl`, `3xl`)
3. **Espaciados**: Los que ya trae Tailwind son suficientes
4. **Border radius**: Definir si el sistema es redondeado (`rounded-xl`) o cuadrado (`rounded-sm`)
5. **Modo**: Dark mode o light mode desde el inicio (cambiar esto después es costoso)

## Archivos que modifica

El Design System en Lovable Cloud vive en:

- `src/index.css` → Variables CSS (`:root { --primary: ... }`)
- `tailwind.config.ts` → Mapeo de variables a clases Tailwind
- `src/components/ui/` → shadcn/ui configura sus componentes desde las variables CSS

## Prompt → ver `prompts/01-design-system.md`

## Cómo verificar que el DS quedó bien

Pedile a Lovable que genere un componente de prueba:

```
Create a test page at /design-test that shows:
- All color swatches (primary, secondary, background, surface, border)
- Typography scale (h1 to h6, body, small)
- A primary button and a secondary button
- A card component with a title and description

This page is only for design validation and will be deleted later.
```

## Señales de alerta

- 🚨 Si el preview tiene colores azules genéricos de Tailwind → El DS no se aplicó
- 🚨 Si shadcn/ui usa sus estilos por defecto → Las variables CSS no están bien mapeadas
