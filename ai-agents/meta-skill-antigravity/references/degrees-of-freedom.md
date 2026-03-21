# Degrees of Freedom (Grados de Libertad)

El éxito de una skill depende de qué tanta libertad le das al agente para ejecutar la tarea.

## Los 3 Niveles

### 1. Alta Libertad (Heurísticas)
**Cuándo usar**: Cuando hay múltiples formas correctas de llegar al resultado y la decisión depende de un contexto muy variable.
**Formato**: Instrucciones en lenguaje natural, principios generales.
**Ejemplo**: "Diseña una UI que se sienta premium y use colores vibrantes".

### 2. Media Libertad (Patrones)
**Cuándo usar**: Cuando existe un patrón preferido, pero permites ajustes menores según la situación.
**Formato**: Pseudo-código, checklists, scripts con parámetros opcionales.
**Ejemplo**: "Usa el componente `Modal` con estos 3 pasos básicos, pero ajusta el trigger según la página".

### 3. Baja Libertad (Determinismo)
**Cuándo usar**: Para tareas críticas, frágiles o propensas a errores humanos donde la consistencia es vital.
**Formato**: Scripts específicos, reglas absolutas ("SIEMPRE X, NUNCA Y").
**Ejemplo**: "Para rotar un PDF, ejecuta `python scripts/rotate.py file.pdf 90`".

## La Regla de la Fragilidad
A mayor fragilidad del proceso, **menores** deben ser los grados de libertad. Si el agente suele "alucinar" en un paso, conviértelo en un script de **Baja Libertad**.
