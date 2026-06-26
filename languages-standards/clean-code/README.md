# clean-code

Skill fundamentada en los principios de "Clean Code" de Robert C. Martin (Uncle Bob) para transformar código meramente funcional en código limpio, legible y mantenible.

## Resumen

Esta skill proporciona pautas rigurosas para mejorar la legibilidad y estructura de nuestro código. Abarca el nombramiento auto-descriptivo de variables y funciones, el diseño de métodos pequeños de responsabilidad única, la eliminación de comentarios redundantes, la gestión estructurada de errores y las pautas del diseño orientado a objetos.

**Insight Clave:** El código limpio es aquel que puede ser leído, comprendido y mejorado por cualquier desarrollador que no sea su autor original. Si necesitas explicar tu código con comentarios detallados, probablemente sea una señal de que debes refactorizarlo.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender la filosofía central y las reglas de diseño.
2. **Consultá** la sección de *Nombres Significativos* y *Funciones* al escribir nuevo código o refactorizar código heredado (legacy).
3. **Revisá** tu código contra la lista de verificación (Implementation Checklist) antes de dar por finalizada una tarea.
4. **Aplicá** las tres leyes de TDD (*Test-Driven Development*) al estructurar tus pruebas unitarias.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Pautas fundamentales sobre nombres descriptivos, tamaño y abstracción de funciones, uso saludable de comentarios, formateo, la Ley de Deméter, manejo de excepciones y principios F.I.R.S.T. de testing.

## Principios Técnicos Clave

1. **Nombres con Revelación de Intención:** Evitar nombres crípticos o abreviaturas confusas (`d` → `elapsedTimeInDays`). Usar sustantivos para clases y verbos para métodos.
2. **Funciones de Responsabilidad Única (SRP):** Las funciones deben ser pequeñas, realizar exactamente una acción y operar bajo un único nivel de abstracción.
3. **Comentarios como Último Recurso:** Expresar la intención a través de código auto-descriptivo en lugar de redactar comentarios aclaratorios para malas implementaciones.
4. **Manejo de Errores Limpio:** Preferir el lanzamiento de excepciones frente a la devolución de códigos de error. Evitar retornar o pasar valores `null` para prevenir fallos inesperados.
5. **Principios F.I.R.S.T. de Pruebas Unitarias:**
   * **F**ast: Pruebas rápidas para ejecución continua.
   * **I**ndependent: Pruebas no dependientes entre sí.
   * **R**epeatable: Ejecutables en cualquier entorno sin fallar.
   * **S**elf-Validating: Resultado booleano claro (pasa o falla).
   * **T**imely: Escritas justo antes del código de producción (TDD).

## Estructura

```
clean-code/
└── SKILL.md                  # Pautas de refactorización y clean code
```

## Skills Relacionadas

- **`software-architecture`** - Para aplicar buenas prácticas a nivel de diseño general de sistemas.
- **`testing-patterns`** - Para profundizar en patrones y metodologías de pruebas de software.
