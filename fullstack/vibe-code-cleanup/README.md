# Vibe-Code Cleanup — Production Refactor Skill

Flujo de trabajo para la limpieza, hardening y optimización incremental de aplicaciones Fullstack construidas de manera rápida o exploratoria (AI vibe-coding) en Next.js, React, Node.js y afines.

## Resumen

Esta habilidad proporciona una metodología quirúrgica y segura para preparar bases de código para producción. El enfoque principal es eliminar archivos muertos, resolver importaciones rotas, consolidar lógica duplicada y auditar variables de entorno, todo ello de forma controlada para garantizar que nada de lo que funciona actualmente se rompa en el proceso.

## Inicio Rápido

Para diagnosticar y mapear la deuda técnica de un proyecto:

### 1. Mapeo y Detección (Reconocimiento)
Ejecuta comandos de búsqueda para listar archivos clave y detectar errores de importación en TypeScript:
```bash
# Listar rutas de Next.js
find . -type f \( -name 'page.js' -o -name 'page.jsx' -o -name 'page.ts' -o -name 'page.tsx' \)

# Buscar errores de tipos e importaciones rotas
npx tsc --noEmit
```

### 2. Ciclo de Validación Continua
Después de realizar cualquier limpieza pequeña, valida inmediatamente el estado de la build:
```bash
npx tsc --noEmit && npm run build
```

## Qué Incluye

- **Filosofía Quirúrgica ("Surgery, not demolition")**: Reglas estrictas para conservar el comportamiento observable de la aplicación.
- **Resolución de Importaciones Rotas**: Corrección prioritaria de referencias antes de realizar cualquier otra limpieza.
- **Consolidación de Lógica en Helpers**: Identificación de lógica repetida en 3 o más lugares (ej. bloques de metadatos SEO o wrappers de fetch) para centralizarlos.
- **Auditoría de Variables de Entorno**: Detección de variables no documentadas y estructuración de archivos `.env.example` sin comprometer secretos.
- **Estrategia de Commits lógicos y pequeños**: Evitar commits masivos mezclando lógica, UI y eliminaciones.

## Conceptos Clave

- **Qué NO limpiar**: Rutas activas indexadas por buscadores, contratos de APIs existentes, modelos de bases de datos (Prisma/SQL) o flujos de autenticación críticos.
- **Comprobación Cruzada (Grep-check)**: Confirmar la ausencia de referencias a un componente o función en todo el proyecto antes de proceder a borrar el archivo físico.

## Estructura de la Habilidad

```
vibe-code-cleanup/
├── SKILL.md                 # Flujo de trabajo detallado y comandos
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [refactor](../refactor/README.md) - Refactorización de código limpio e incremental.
- [clean-code](../../languages-standards/clean-code/README.md) - Estándares de legibilidad y buenas prácticas.
- [nextjs-production-debugger](../frontend-ui/nextjs-production-debugger/README.md) - Diagnóstico y depuración de incidencias en producción.
