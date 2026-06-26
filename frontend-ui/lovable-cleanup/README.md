# lovable-cleanup

Skill especializada en auditar y limpiar los proyectos generados por la plataforma Lovable (lovable.dev), eliminando dependencias de andamiaje, marcas, archivos temporales y dependencias no utilizadas.

## Resumen

Esta skill ayuda a eliminar la huella digital que Lovable inyecta en los proyectos Vite + React + shadcn/ui. Se encarga de remover `lovable-tagger` del entorno de desarrollo, renombrar nombres de proyectos genéricos en `package.json`, limpiar meta-tags e íconos en `index.html`, depurar dependencias Radix no utilizadas y suprimir archivos markdown explicativos redundantes.

**Insight Clave:** No elimines a ciegas todas las dependencias Radix. El paquete `@radix-ui/react-slot` debe conservarse siempre, ya que es requerido internamente por la mayoría de los componentes de shadcn/ui mediante la propiedad `asChild`.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para conocer las 14 áreas de huellas digitales de Lovable y el orden recomendado de ejecución.
2. **Ejecutá** una búsqueda global de referencias en tu terminal:
   ```bash
   grep -rn "lovable\|Lovable" --exclude-dir=node_modules .
   ```
3. **Remové** la dependencia de desarrollo `lovable-tagger` y desactiva su plugin en `vite.config.ts`.
4. **Depurá** y borra los archivos markdown explicativos del directorio raíz (`CLEANUP_SUMMARY.md`, `DEPLOYMENT_GUIDE.md`, etc.).
5. **Validá** que el proyecto compile limpiamente ejecutando `npm run build`.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía paso a paso para limpiar el README, package.json, configuración de Vite, assets públicos, variables de entorno, gitignore, dependencias sin usar, y plantilla de reporte de salida.

## Estructura

```
lovable-cleanup/
└── SKILL.md                  # Pautas de limpieza de Lovable
```

## Skills Relacionadas

- **`senior-frontend`** - Para analizar el tamaño de los bundles de distribución resultantes.
- **`shadcn`** - Para el mantenimiento y adición de nuevos componentes limpios.
