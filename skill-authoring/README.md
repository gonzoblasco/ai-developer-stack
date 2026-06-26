# ✍️ Playbook de Creación de Skills

Este playbook detalla los estándares, pautas y filosofías centrales para la creación de skills de agentes de IA predecibles y efectivas.

## Skills Disponibles

| Skill | Descripción | Target |
| --- | --- | --- |
| [writing-great-skills](writing-great-skills/SKILL.md) | Vocabulario, jerarquía de información y principios para escribir skills predecibles | Ingeniería de Agentes |

## Filosofía

1. **La predictibilidad es clave**: Una skill existe para hacer que el proceso de ejecución del agente sea predecible y consistente.
2. **Higiene de la ventana de contexto**: Balanceá las configuraciones invocadas por el modelo frente a las invocadas por el usuario para optimizar la carga del contexto.
3. **Divulgación progresiva**: Mantené `SKILL.md` limpio y conciso empujando las referencias profundas y los ejemplos a archivos/carpetas separados.
4. **Palabras clave (Leading Words)**: Aprovechá los conceptos preentrenados del modelo (por ejemplo, *red loop*, *Gemba*) para anclar comportamientos complejos en menos tokens.
