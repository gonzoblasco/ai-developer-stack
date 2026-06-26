# accesslint-audit

Skill especializada en la detección y corrección automatizada de problemas de accesibilidad web (WCAG 2.2) mediante herramientas de análisis estático y dinámico (Chrome DevTools Protocol - CDP).

## Resumen

Esta skill opera en dos modalidades: **Report Mode** (inspección pasiva y reporte priorizado de vulnerabilidades de accesibilidad) y **Fix Mode** (ciclo iterativo de auditoría, edición y verificación de código en caliente). Soporta auditorías sobre aplicaciones en ejecución conectándose a sesiones de depuración de Chrome, y auditorías estáticas sobre archivos HTML o JSX.

**Insight Clave:** Prioriza siempre la auditoría sobre el DOM en vivo (`audit_live`), ya que refleja el estado de renderizado real de la aplicación incluyendo lógica de JavaScript e hidratación, cayendo a análisis estático de HTML solo como último recurso.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la diferencia de flujos entre Report Mode y Fix Mode.
2. **Ejecutá** una auditoría en vivo en tu URL o entorno local:
   ```bash
   # (Se invoca mediante las herramientas del agente de depuración)
   ```
3. **Analizá** los resultados priorizados (Critical, Serious, Moderate, Minor) estructurados bajo el estándar de reporte de la skill.
4. **Implementá** el ciclo de corrección en Fix Mode: realiza la corrección mecánica sobre el archivo JSX/TSX fuente y ejecuta la comparación de diferencias para verificar que la regresión haya desaparecido.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas operacionales, flujo de auditoría dinámico/estático, plantilla estándar de reportes y ciclo de vida de correcciones.

## Modos de Operación

*   **Report Mode:** Genera un diagnóstico completo agrupando fallos repetidos por regla, vinculando la violación a la especificación WCAG y sugiriendo la corrección, sin alterar ningún archivo.
*   **Fix Mode (Audit-Edit-Verify):**
    1. *Baseline:* Registra los fallos actuales.
    2. *Plan & Edit:* Modifica el código fuente localizando referencias precisas.
    3. *Verify:* Corre una auditoría de control diferencial para garantizar el éxito del fix.

## Estructura

```
accesslint-audit/
└── SKILL.md                  # Contenido metodológico principal
```

## Skills Relacionadas

- **`accessibility-audit`** - Para conceptos y pautas de diseño accesible generales.
- **`wcag-audit-patterns`** - Para consultar la matriz extendida de cumplimiento WCAG 2.2 AA/AAA.
- **`ui-a11y`** - Para auditoría móvil y componentes interactivos específicos.
