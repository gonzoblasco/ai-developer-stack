# rag-expert

Estrategias y patrones de código para construir sistemas de Recuperación Aumentada por Generación (RAG) de grado de producción.

## Resumen

Esta skill proporciona las directrices técnicas para asegurar la calidad de la recuperación de información antes de enviarla a los modelos de lenguaje. Enfatiza técnicas de particionado semántico (semantic chunking), búsquedas híbridas y procesos de re-ordenamiento (reranking).

**Insight Clave:** La calidad de la generación del modelo depende enteramente de la precisión de los documentos recuperados (*"Garbage In, Garbage Out"*).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender los retos de la recuperación semántica y las métricas de evaluación.
2. **Implementá** un pipeline de procesamiento robusto usando las plantillas incluidas:
   * **Particionado:** [semantic_chunking.py](templates/semantic_chunking.py) para dividir textos según coherencia semántica en lugar de longitud de caracteres fija.
   * **Búsqueda:** [hybrid_search.py](templates/hybrid_search.py) para combinar la precisión conceptual de los embeddings vectoriales con palabras clave específicas (BM25).
3. **Aplicá** Reranking a tus resultados para optimizar la relevancia de los elementos posicionados en el top K.
4. **Medí** el desempeño de tu sistema con [retrieval_eval.py](templates/retrieval_eval.py).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas generales del flujo RAG y guardrails.
- **[embedding_models.md](references/embedding_models.md)** - Guía comparativa para elegir el modelo de representación vectorial adecuado (código fuente, textos multilingües, etc.).

### Plantillas de Código Ejecutable

- **[semantic_chunking.py](templates/semantic_chunking.py)** - Algoritmo para fragmentar documentos usando diferencias de similitud de oraciones.
- **[hybrid_search.py](templates/hybrid_search.py)** - Integración de motores de búsqueda de palabras clave y bases de datos vectoriales.
- **[retrieval_eval.py](templates/retrieval_eval.py)** - Evaluador de métricas de precisión y recall sobre conjuntos de prueba.

## Principios Técnicos Fundamentales

1. **Búsqueda Híbrida Obligatoria:** La búsqueda vectorial pura falla al buscar identificadores exactos, códigos de error o nombres propios. Combinar con índices tradicionales de palabras clave es mandatorio.
2. **Uso Indispensable de Reranking:** Los modelos de embeddings no garantizan que el documento más útil sea el primero de la lista. Un paso secundario de ordenamiento (Cross-Encoders) maximiza la relevancia.
3. **Chunking Inteligente:** Fragmentar contenido basándose en el cambio del tema lingüístico previene la pérdida de contexto en bordes arbitrarios de palabras.

## Estructura

```
rag-expert/
├── SKILL.md                  # Pautas de arquitectura
├── templates/                # Código y scripts para chunking, búsqueda y evaluación
└── references/               # Guía de selección de modelos y bases vectoriales
```

## Skills Relacionadas

- **`ai-agents-architect`** - Para diseñar bases de conocimiento y memoria a largo plazo basadas en RAG.
- **`agent-tool-builder`** - Para diseñar herramientas que consulten almacenes vectoriales externos.
