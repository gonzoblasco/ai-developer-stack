# Web Artifacts Builder (Antigravity & Internal Docs)

Guía y scripts de automatización para construir artefactos interactivos de frontend y páginas de documentación interna auto-contenidas en un único archivo HTML.

## Resumen

Esta habilidad proporciona herramientas para inicializar, desarrollar, empaquetar y desplegar aplicaciones completas de React en un solo archivo `bundle.html` autoejecutable. La pila tecnológica predefinida combina React 18, TypeScript, Vite, Tailwind CSS y componentes de shadcn/ui. El empaquetamiento se realiza con Parcel e inlining de recursos para facilitar su carga en el entorno de desarrollo de Antigravity.

## Inicio Rápido

### 1. Inicializar el proyecto del artefacto
```bash
bash scripts/init-artifact.sh mi-artefacto
cd mi-artefacto
```

### 2. Desarrollar
Modifica el código generado en la carpeta del proyecto. Puedes instalar dependencias adicionales si es necesario.

### 3. Empaquetar todo en un único HTML
```bash
bash scripts/bundle-artifact.sh
```
Este comando generará el archivo `bundle.html` con todo el JavaScript, CSS y assets enlazados en línea (inlined).

## Qué Incluye

- **Script de Inicialización (`init-artifact.sh`)**: Crea una estructura completa con Vite, Tailwind, alias de rutas (`@/`), Node 18+ y más de 40 componentes de shadcn/ui listos para usar.
- **Script de Empaquetamiento (`bundle-artifact.sh`)**: Configura Parcel, resuelve los aliases de TypeScript y compila todos los recursos estáticos en una única página HTML.
- **Pautas Antisalpicaduras (Anti-slop)**: Reglas estéticas estrictas para evitar diseños excesivamente genéricos (evitar el uso de tipografía Inter por defecto, degradados purpuras y layouts completamente centrados sin justificación).

## Conceptos Clave

- **Auto-contenido**: El archivo HTML resultante no debe depender de CDN externos o scripts remotos para funcionar, garantizando su portabilidad fuera de línea.
- **Evitar latencias de test**: Se recomienda visualizar y probar el artefacto después de su generación en lugar de ejecutar suites de pruebas complejas previas que retrasen el despliegue del componente.

## Estructura de la Habilidad

```
web-artifacts-builder/
├── SKILL.md                 # Flujo de trabajo y especificaciones de empaquetado
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [shadcn](../shadcn/README.md) - Documentación e integración de componentes UI.
- [tailwind-patterns](../tailwind-patterns/README.md) - Configuración y optimización de estilos visuales.
- [frontend-dev-guidelines](../frontend-dev-guidelines/README.md) - Buenas prácticas de desarrollo frontend.
