# nestjs-expert

Skill experta en el framework NestJS para el diseño y construcción de aplicaciones del lado del servidor (backend) escalables y con arquitectura empresarial.

## Resumen

Esta skill proporciona soporte avanzado en la arquitectura modular de NestJS, inyección de dependencias, ciclo de vida de peticiones (guards, interceptors, pipes, middleware), estrategias de autenticación (JWT/Passport), integraciones de bases de datos y metodologías de testing (unitario y E2E).

**Insight Clave:** Respeta siempre los límites arquitectónicos de NestJS. Evita atajos o parches que rompan la estructura modular y vigila de cerca la introducción de dependencias circulares al inyectar servicios.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender el flujo de diagnóstico y la correspondencia con expertos de soporte especializados.
2. **Consultá** la lista de verificación exhaustiva en [references/checklist.md](references/checklist.md) antes de enviar cambios de código a producción.
3. **Analizá** y resuelve errores típicos (como fallas de conexión TypeORM o inyecciones no resueltas) en [references/troubleshooting.md](references/troubleshooting.md).
4. **Implementá** patrones de código comunes (decorators personalizados, módulos dinámicos) usando la guía de [references/patterns.md](references/patterns.md).
5. **Validá** tus cambios de forma secuencial:
   ```bash
   npm run build          # 1. Compilación y Typecheck
   npm run test           # 2. Tests unitarios
   npm run test:e2e       # 3. Tests E2E
   ```

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Flujo de diagnóstico, comandos de verificación rápida del entorno y métricas de éxito.
- **[architecture-decisions.md](references/architecture-decisions.md)** - Árboles de decisión para la selección de ORMs, estrategias de Autenticación, Caching y estructuración de módulos.
- **[patterns.md](references/patterns.md)** - Plantillas de código para decoradores de usuario, inyección dinâmica y setups de mocks para testing.
- **[performance.md](references/performance.md)** - Estrategias de optimización, manejo de streams y caché en NestJS.
- **[checklist.md](references/checklist.md)** - Lista de control con más de 30 puntos críticos de revisión de código (seguridad, consistencia y arquitectura).
- **[troubleshooting.md](references/troubleshooting.md)** - Soluciones detalladas a más de 17 errores y advertencias comunes del compilador y runtime de NestJS.

## Principios de Éxito en NestJS

*   **Modularidad Estricta:** Encapsula la lógica relacionada en módulos específicos (`@Module`). Expón solo lo necesario mediante `exports` para proteger los límites del sistema.
*   **Ciclo de Vida Claro:** Utiliza Pipes para validaciones y transformaciones de datos de entrada (`ValidationPipe`), Guards para autorización (`AuthGuard`) e Interceptors para formateo de respuestas de salida.
*   **Cero Dependencias Circulares:** Si dos servicios se necesitan mutuamente, refactoriza la lógica compartida a un tercer servicio o utiliza `forwardRef()` de forma consciente.
*   **Testing Aislado:** Aprovecha `Test.createTestingModule()` para emular dependencias complejas mediante proveedores mockeados en tus pruebas unitarias.

## Estructura

```
nestjs-expert/
├── SKILL.md                  # Reglas del pipeline de NestJS
├── implementation_plan.md    # Planificación del desarrollo de la skill
├── task.md                   # Control de tareas internas
└── references/               # Guías en profundidad sobre arquitectura, patrones y fallas
```

## Skills Relacionadas

- **`api-patterns`** - Para diseñar esquemas REST y GraphQL estructurados que se implementarán en NestJS.
- **`prisma-expert`** - Para integrar el acceso a datos mediante Prisma Client de manera óptima.
- **`postgres-best-practices`** - Para ajustar las consultas de base de datos a nivel de infraestructura.
