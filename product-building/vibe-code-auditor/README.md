# Vibe Code Auditor

Habilidad de auditoría de arquitectura y calidad de software. Especializada en evaluar código generado mediante iteraciones rápidas o asistencia de IA (vibe-coding) para determinar si es robusto, mantenible y apto para producción.

## Resumen

Esta habilidad actúa como un arquitecto revisor senior. Evalúa bases de código completas o fragmentos a través de 7 dimensiones clave (Arquitectura, Consistencia, Robustez, Riesgos de Producción, Seguridad, Código Muerto/Alucinado y Puntos Calientes de Deuda Técnica), emitiendo una calificación de preparación para producción (Production Readiness Score) y un plan priorizado de refactorización.

## Inicio Rápido

Para auditar un archivo o fragmento de código:

1. **Escaneo Rápido (Quick Scan)**: Identifica tecnologías y busca alertas obvias (credenciales quemadas, bloques de captura de error vacíos, etc.).
2. **Auditoría de 7 Dimensiones**: Inspecciona el código buscando fallos de seguridad (inyección SQL, llamadas sin timeout), código muerto o funciones de complejidad excesiva (>50 líneas).
3. **Generar Reporte**: Lanza el informe estructurado detallando los hallazgos críticos (deben solucionarse antes de producción), de alto riesgo y problemas menores.

## Qué Incluye

- **Atajos de Reconocimiento de Patrones (Pattern Recognition)**: Heurísticas rápidas para buscar sentencias propensas a fallos (ej: `eval()`, `except Exception:`, string concatenado en SQL).
- **Las 7 Dimensiones de Auditoría**:
  1. Arquitectura y Diseño.
  2. Consistencia y Mantenibilidad.
  3. Robustez y Manejo de Errores.
  4. Riesgos de Producción.
  5. Seguridad y Aislamiento.
  6. Código Muerto o Alucinado.
  7. Puntos Calientes de Deuda Técnica.
- **Fórmula de Calificación (Scoring Algorithm)**: Algoritmo para puntuar del 0 al 100 la viabilidad del despliegue en producción restando penalizaciones por fallos encontrados.

## Conceptos Clave

- **Cirugía, no demolición**: No sugerir reescrituras estéticas masivas; recomendar las correcciones mínimas requeridas para mitigar riesgos reales y palpables.
- **Evitar alucinaciones**: Cada hallazgo reportado en la auditoría debe estar referenciado a una línea de código y archivo exacto en el repositorio.

## Estructura de la Habilidad

```
vibe-code-auditor/
├── SKILL.md                 # Heurísticas de auditoría, dimensiones y plantilla de reporte
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [vibe-code-cleanup](../../fullstack/vibe-code-cleanup/README.md) - Limpieza y refactorización incremental de bases de código.
- [refactor](../../fullstack/refactor/README.md) - Reestructuración de lógica sin cambio de comportamiento.
- [security-audit](../../backend-infra/security-audit/README.md) - Escaneo y mitigación de vulnerabilidades OWASP.
