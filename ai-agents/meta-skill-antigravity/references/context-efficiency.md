# Context Efficiency (Eficiencia de Contexto)

El context window es un recurso finito y compartido. Una skill eficiente maximiza el valor por token.

## Principios de Ahorro

1. **Antigravity ya es inteligente**: No expliques conceptos básicos de programación o lógica a menos que sea un truco muy específico.
2. **Ejemplos > Explicaciones**: Un bloque de código `Antes/Después` vale más que tres párrafos de teoría.
3. **Progressive Disclosure**: No metas todo en `SKILL.md`. Si algo es una referencia de API de 2000 líneas, ponla en `references/`. El agente solo la leerá si la necesita.
4. **Evita la redundancia**: No repitas en `SKILL.md` lo que ya está claro en los nombres de los scripts o en archivos de referencia.

## Keywords Clave (Triggering)
La `description` en el frontmatter es lo único que el sistema lee para decidir si activa la skill.
- Sé específico: Incluye nombres de librerías, tipos de error o comandos.
- Evita descripciones genéricas como "Ayuda con Python".
- Usa: "Creación de APIs con FastAPI y autenticación OAuth2".
