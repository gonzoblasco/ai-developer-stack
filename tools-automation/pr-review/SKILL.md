---
name: pr-review
description: Actuar como un linter cognitivo pre-merge. Analiza el diff completo de la rama contra convenciones, correctitud, cobertura de tests, seguridad y performance.
risk: unknown
source: community
date_added: "2026-06-26"
---

# Skill: PR Review (Linter Cognitivo Pre-Merge)

## Propósito

Actuar como un segundo par de ojos automatizado. Analiza el diff completo de la rama (`git diff main...HEAD`) contra las convenciones del repositorio y las buenas prácticas de ingeniería antes de consolidar el código.

---

## Dimensiones de la Auditoría

### 1. Correctitud Funcional y Edge Cases

- Buscar rutas de error no manejadas (promesas sin `.catch` o `try/catch`, valores `null`/`undefined` que puedan romper el flujo).
- Detectar posibles condiciones de carrera (_race conditions_) o estados inconsistentes en el cliente/servidor.

### 2. Cobertura de Pruebas (Tests)

- Validar que la lógica de negocio core o los nuevos endpoints tengan sus correspondientes archivos de prueba.
- La falta de cobertura en componentes críticos es considerada **bloqueante**.

### 3. Convenciones, Arquitectura y Limpieza

- Contrastar los cambios contra las definiciones arquitectónicas del repositorio.
- Detectar `console.log` residuales, comentarios de depuración (`// TODO: remover esto`) o código muerto.

### 4. Seguridad de Capa Temprana

- **Secrets:** Prohibir terminantemente credenciales, tokens o API keys hardcodeadas.
- **Injections:** Verificar que las entradas de usuario estén tipadas, validadas o sanitizadas antes de tocar bases de datos u operaciones de sistema.
- **Auth guards:** Asegurar que cada ruta nueva cuente con su middleware o validación de sesión correspondiente.

### 5. Eficiencia y Rendimiento (Performance)

- Identificar iteraciones innecesarias, mutaciones pesadas en hilos principales o consultas de base de datos ineficientes (ej. patrón N+1 evitable).

---

## Estructura Estricta del Reporte de Salida

El agente debe renderizar la revisión utilizando exactamente esta plantilla Markdown:

```markdown
## 🔍 Reporte de Revisión de Código — [Rama/Task]

### ✅ Aspectos Positivos

- [Puntos fuertes del diseño, modularidad o buenas prácticas aplicadas]

### 🔴 Hallazgos Bloqueantes (Requieren Corrección Obligatoria)

- **[Archivo:Línea]** — [Descripción del problema de seguridad, build o lógica severa]

### 🟡 Mejoras Sugeridas (No Bloquean el Merge)

- **[Archivo:Línea]** — [Recomendación de legibilidad, optimización leve o refactor futuro]

### 🔵 Observaciones Técnicas / Deuda

- [Notas contextuales sobre arquitectura o comportamiento a largo plazo]

### 🛠️ VEREDICTO FINAL

[APPROVED / REQUEST CHANGES]
```
