# Product Manager Toolkit

Repositorio de herramientas operativas, scripts de análisis y frameworks prácticos de gestión de producto para automatizar la priorización y sintetizar hallazgos de descubrimiento.

## Resumen

Esta habilidad amplía el rol de Product Manager mediante scripts en Python para priorizar funcionalidades bajo el modelo RICE (`rice_prioritizer.py`) y procesar transcripciones de entrevistas de usuarios utilizando procesamiento de lenguaje natural (`customer_interview_analyzer.py`). Incluye además plantillas avanzadas de especificaciones de requisitos (PRD Standard, Agile Epic y One-Pagers).

## Inicio Rápido

### 1. Priorización de Backlog con RICE
Genera una plantilla de ejemplo o corre la priorización indicando la capacidad máxima de esfuerzo en meses/persona por trimestre:
```bash
python scripts/rice_prioritizer.py sample
python scripts/rice_prioritizer.py sample_features.csv --capacity 15
```

### 2. Análisis NLP de Entrevistas de Clientes
Sintetiza de forma automática dolores y requerimientos a partir de una transcripción de chat/entrevista:
```bash
python scripts/customer_interview_analyzer.py interview_transcript.txt
```

## Qué Incluye

- **Scripts de Automatización PM**:
  - `rice_prioritizer.py`: Cálculo de RICE, asignación de Quick Wins frente a Big Bets, balanceo de portafolios y salidas JSON/CSV.
  - `customer_interview_analyzer.py`: Extracción automática de puntos de dolor (pain points), peticiones de features, mapeo de Jobs-to-be-Done (JTBD) y análisis de sentimiento.
- **Plantillas de PRD (`references/prd_templates.md`)**: Formato Completo de 11 secciones, One-Page PRD ágil y briefs de exploración técnica.
- **Frameworks de Negocio**: MoSCoW, Matrices de Valor-Esfuerzo, e Hipótesis de Experimentos.
- **Funnels y KPIs**: Directrices para el North Star Metric, análisis de conversión AARRR e indicadores de adopción de features.

## Conceptos Clave

- **Priorización RICE**:
  `Score = (Reach × Impact × Confidence) / Effort`
  - Reach (Alcance de usuarios por trimestre).
  - Impact (Multiplicador de 0.25x a 3x).
  - Confidence (Certidumbre de 50% a 100%).
  - Effort (Esfuerzo en meses/persona).
- **Evitar la Fábrica de Features (Feature Factory)**: No liberar funcionalidades sin definir previamente las métricas de éxito y medir su impacto posterior.

## Estructura de la Habilidad

```
product-manager-toolkit/
├── SKILL.md                 # Guía general de uso de herramientas
├── scripts/
│   ├── rice_prioritizer.py          # Script de cálculo y roadmap RICE
│   └── customer_interview_analyzer.py # Script NLP de análisis de entrevistas
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [product-manager](../product-manager/README.md) - Guía teórica general y métricas financieras SaaS.
- [brainstorming](../brainstorming/README.md) - Aclaración e ideación previa de requerimientos.
- [micro-saas-launcher](../micro-saas-launcher/README.md) - Enfoques y tracción para MVPs de negocio.
