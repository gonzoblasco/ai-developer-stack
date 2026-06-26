# Plan Writing

Framework de planificación estructurada de tareas técnicas enfocado en la simplicidad, la especificidad y la definición clara de criterios de verificación por cada paso.

## Resumen

Esta habilidad define las pautas para escribir hojas de ruta técnicas funcionales. Prohíbe el uso de plantillas rígidas e impersonales, obligando a generar planes adaptados específicamente al tipo de proyecto (Frontend, Backend, Mobile, etc.) y limitando el alcance a un máximo de 10 tareas atómicas y verificables por plan.

## Inicio Rápido

Para redactar un plan de desarrollo:

1. **Definir el objetivo**: Escribe una oración directa que resuma qué se construirá o solucionará.
2. **Desglosar en tareas atómicas**: Lista un máximo de 5 a 10 tareas específicas (cada una debe tomar de 2 a 5 minutos) y asócialas inmediatamente a un método de validación claro:
   ```markdown
   - [ ] Tarea 1: Modificar `Navbar.tsx` para agregar botón de logout → Verificar: Iniciar `npm run dev`, dar clic al botón, ver redirección.
   ```
3. **Guardar en la raíz**: Almacena el plan con la nomenclatura `{task-slug}.md` en la raíz del proyecto. **Nunca** lo guardes en subcarpetas temporales u ocultas.

## Qué Incluye

- **Principios de Desglose de Tareas**: Tareas cortas e independientes con orden lógico (las dependencias primero, la verificación final al último).
- **Enfoque Pragmático (Keep it Short)**: Evitar la creación de planes verbosos de más de una página.
- **Tipos de Proyecto dinámicos**: Planificación diferenciada para nuevos desarrollos (MVP, stack), características adicionales (archivos afectados, dependencias) y parches de errores (causa raíz, testing de regresión).
- **Estructura Flexible Recomendada**: Sección de meta (Goal), lista de verificación de tareas (Tasks), y condiciones de término (Done When).

## Conceptos Clave

- **Especificidad frente a Generalidades**: Evitar descripciones vagas (ej: "Añadir estilos"). Preferir instrucciones técnicas directas (ej: "Añadir clases Tailwind CSS a `Header.tsx`").
- **Verificación Práctica**: Definir la finalización mediante acciones reales (ej: llamadas `curl`, clicks en el navegador) en lugar de aserciones conceptuales de código.

## Estructura de la Habilidad

```
plan-writing/
├── SKILL.md                 # Principios y reglas de redacción de planes
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [not-a-vibe-coder](../not-a-vibe-coder/README.md) - Planificación macro de proyectos nuevos.
- [brainstorming](../brainstorming/README.md) - Clarificación de requisitos previo al plan.
- [new-task](../new-task/README.md) - Inicialización técnica del flujo de desarrollo de tareas.
