# commit

Skill para formatear y crear mensajes de confirmación de Git en cumplimiento con la especificación de Conventional Commits y las directivas del proyecto.

## Resumen

Esta skill garantiza que cada aporte al historial de Git sea legible, auditable y automatizable para generación de notas de lanzamiento (CHANGELOG). Ofrece directrices de tipología (`feat`, `fix`, `refactor`, `test`, `docs`, `chore`, `perf`, `ci`), criterios de definición de scopes y pautas para la orquestación híbrida del commit en terminal o IDE.

**Insight Clave:** El mensaje de commit debe explicar la intención y el contexto de negocio (el "por qué" cambió), no el código en sí mismo (el "cómo"). El título de la primera línea no debe superar los 72 caracteres y debe escribirse en minúsculas y modo imperativo.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la estructura de los mensajes de commit, reglas gramaticales y precondiciones.
2. **Ejecutá** una revisión de los archivos a incluir en tu terminal:
   ```bash
   git status
   git diff --staged
   ```
3. **Redactá** o automatizá el mensaje de commit bajo el formato:
   ```text
   tipo(scope): descripción corta en minúsculas y modo imperativo
   ```

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Guía de formato, limitaciones de longitud, tipología válida, flujo de orquestación en CLI/IDE y ejemplos detallados de buenos y malos mensajes.

## Tipologías de Conventional Commits Soportadas

*   `feat`: Nueva funcionalidad para el usuario.
*   `fix`: Corrección de un bug.
*   `refactor`: Cambios de código sin alterar comportamiento (limpieza, optimización estructural).
*   `test`: Adición o corrección de pruebas unitarias/E2E.
*   `docs`: Cambios exclusivos en comentarios o documentación técnica Markdown.
*   `chore`: Mantenimiento, dependencias o configuraciones.
*   `perf`: Optimización de rendimiento/memoria.
*   `ci`: Ajustes en pipelines o scripts de despliegue continuo.

## Estructura

```
commit/
└── SKILL.md                  # Pautas de commits estándar
```

## Skills Relacionadas

- **`clean-code`** - Para asegurar que los cambios que se van a commitear cumplan con los estándares de legibilidad.
- **`testing-patterns`** - Para validar los archivos de test incluidos en los commits de tipo `test`.
