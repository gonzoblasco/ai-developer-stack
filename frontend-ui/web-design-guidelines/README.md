# Web Interface Guidelines

Guía de auditoría y validación automatizada para asegurar que las páginas y componentes web cumplan con las directrices de interfaz de Vercel Labs (Web Interface Guidelines).

## Resumen

Esta habilidad permite revisar archivos y directorios de frontend comparándolos dinámicamente contra un conjunto actualizado de reglas estéticas y de interacción web hospedado en Vercel Labs. El análisis produce un reporte terso en formato `archivo:línea` señalando violaciones específicas de estilo, estructura de DOM y usabilidad.

## Inicio Rápido

Para llevar a cabo una auditoría de directrices:

1. **Obtener las reglas actualizadas**: Consume el recurso oficial de reglas mediante un lector de URLs HTTP:
   ```
   https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md
   ```
2. **Revisar los archivos**: Procesa los componentes designados utilizando las directrices descargadas.
3. **Reportar**: Genera el listado estructurado de inconsistencias en el formato estándar `file:line` para su fácil depuración en el editor de código.

## Qué Incluye

- **Descarga Dinámica**: Instrucciones para jalar reglas frescas en tiempo de ejecución, evitando la obsolescencia de patrones de diseño.
- **Formato Terso de Salida**: Formateo de hallazgos para integraciones con linters y terminales.

## Conceptos Clave

- **Cumplimiento de Estilo Vercel**: Reglas orientadas a la sobriedad visual, tipografías legibles y manejo asertivo de layouts interactivos.
- **Análisis de Archivos Específicos**: El flujo solicita al usuario los archivos exactos a evaluar si no se proveen mediante una máscara o patrón de búsqueda.

## Estructura de la Habilidad

```
web-design-guidelines/
├── SKILL.md                 # Guía y URL del origen de las directrices
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [ui-review-nextjs-tailwind](../ui-review-nextjs-tailwind/README.md) - Revisiones de estructura Next.js y Tailwind CSS.
- [frontend-dev-guidelines](../frontend-dev-guidelines/README.md) - Pautas y convenciones generales de frontend.
