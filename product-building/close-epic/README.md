# Close Epic (Ritual de Consolidación y Versionado)

Metodología y secuencia inalterable de pasos para gobernar la finalización formal de un bloque de desarrollo estratégico (Epic) en Git.

## Resumen

Esta habilidad define un ritual ordenado para estructurar el cierre de tareas críticas de negocio (Epics). Abarca auditorías de seguridad previas, consolidación del historial de cambios (`CHANGELOG.md`), etiquetado de versiones (`git tag`), integraciones limpias tipo `--no-ff` (no-fast-forward), y el resguardo de la memoria del repositorio sin eliminar ramas.

## Inicio Rápido

Para proceder al ritual de cierre de una Epic (ej. Epic `E1` - Autenticación):

1. **Auditoría de seguridad**: Invoca el escaneo de seguridad en todos los endpoints nuevos.
2. **Consolidar Logs**: Mueve los cambios pendientes al bloque de versión del `CHANGELOG.md` y actualiza `AGENT_TASKS.md` marcando el Epic con un `✅`.
3. **Integración en main**:
   ```bash
   git checkout main
   git pull origin main
   git merge --no-ff epic/e1-auth -m "merge: fusionar epic E1 - Autenticación"
   git tag -a E1-complete -m "Release estable del Epic 1"
   git push origin main --tags
   ```

## Qué Incluye

### Los 7 Pasos Secuenciales
1. **Auditoría de Seguridad Macro**: Escaneo obligatorio de vulnerabilidades.
2. **Consolidación del CHANGELOG**: Agrupación bajo versión semántica semver oficial.
3. **Actualización de Historial**: Registro de lecciones aprendidas en `AGENT_TASKS.md`.
4. **Commit Exclusivo de Documentación**: Commit enfocado únicamente en logs de control (`docs: cerrar E[N] formalmente`).
5. **Integración No-Fast-Forward**: Fusión que conserva la historia gráfica de la rama en Git.
6. **Tag de Git Permanente**: Generación de un punto de restauración inmutable.
7. **Reporte Ejecutivo**: Resumen de endpoints asegurados y estado final.

## Conceptos Clave

- **No auto-delete de ramas**: Conservar las ramas de los Epics locales y remotas de forma intencional como memoria pedagógica y técnica del proyecto.
- **Merge --no-ff**: Forzar la creación de un commit de merge para identificar visualmente dónde inicia y finaliza un Epic en el árbol de Git.

## Estructura de la Habilidad

```
close-epic/
├── SKILL.md                 # Secuencia del ritual de cierre
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [pr](../pr/README.md) - Preparación de Pull Requests individuales.
- [security-audit](../../backend-infra/security-audit/README.md) - Auditorías de vulnerabilidades y seguridad del backend.
