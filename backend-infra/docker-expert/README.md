# docker-expert

Skill experta en contenedorización con Docker, optimización de imágenes, seguridad de contenedores y orquestación con Docker Compose.

## Resumen

Esta skill ayuda a diseñar, optimizar y asegurar contenedores Docker para entornos de desarrollo y producción. Domina la creación de construcciones multi-etapa (multi-stage builds), la reducción del tamaño de imágenes, la configuración de usuarios no-root y la orquestación multicontenedor mediante Docker Compose.

**Insight Clave:** Una imagen Docker optimizada separa dependencias del código fuente para aprovechar la caché de capas de compilación, utiliza imágenes base mínimas (como Alpine o Distroless) y no corre procesos como root.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender los comandos de diagnóstico y la lista de pautas de integración.
2. **Consultá** la guía de revisión de calidad en [references/checklists.md](references/checklists.md).
3. **Analizá** y soluciona problemas comunes de redes o volúmenes consultando [references/troubleshooting.md](references/troubleshooting.md).
4. **Implementá** plantillas estándar copiando los ejemplos provistos en `examples/` (como Dockerfiles multi-etapa o archivos Compose de producción).

## Qué Incluye

### Documentación de Referencia

- **[SKILL.md](SKILL.md)** - Guía metodológica, comandos de validación de entornos y directrices de delegación.
- **[checklists.md](references/checklists.md)** - Checklist para revisión de Dockerfiles, Compose y configuraciones de seguridad.
- **[troubleshooting.md](references/troubleshooting.md)** - Diagnósticos y soluciones para fallas de permisos, redes y límites de recursos.

### Ejemplos Prácticos de Configuración

- **[Dockerfile.multistage](examples/Dockerfile.multistage)** - Plantilla de construcción multi-etapa para separar compilación y runtime.
- **[Dockerfile.security](examples/Dockerfile.security)** - Ejemplo con usuario no-root, variables de entorno seguras y hardening.
- **[Dockerfile.distroless](examples/Dockerfile.distroless)** - Contenedor seguro y ultraligero usando imágenes distroless.
- **[build-cache.dockerfile](examples/build-cache.dockerfile)** - Optimización de caché de capas usando montajes de caché (`--mount=type=cache`).
- **[compose.dev.yaml](examples/compose.dev.yaml)** - Docker Compose para desarrollo local con hot-reload y mapeo de volúmenes de código.
- **[compose.prod.yaml](examples/compose.prod.yaml)** - Docker Compose de producción con límites de CPU/Memoria, healthchecks y redes aisladas.

## Principios Técnicos Clave

1. **Optimización de Caché de Capas:** Copiar primero los manifiestos de dependencias (por ejemplo, `package.json` o `requirements.txt`) e instalarlas antes de copiar el código fuente de la aplicación.
2. **Seguridad no-root:** Crear explícitamente un usuario y grupo del sistema dentro del contenedor y cambiar a él usando la instrucción `USER` para evitar escalamientos de privilegios.
3. **Imágenes Mínimas (Distroless / Alpine):** Reducir la superficie de ataque eliminando shells e intérpretes innecesarios en la imagen de producción final.
4. **Secretos Seguros:** No guardar credenciales ni llaves API en variables de entorno fijas en el Dockerfile; usar montajes de secretos de BuildKit (`--mount=type=secret`) o Docker Secrets.

## Estructura

```
docker-expert/
├── SKILL.md                  # Pautas metodológicas generales
├── references/               # Guías de troubleshooting y calidad
└── examples/                 # Plantillas de Dockerfile y Compose
```

## Skills Relacionadas

- **`postgres-best-practices`** - Para orquestar bases de datos PostgreSQL persistentes con Compose.
- **`nestjs-expert`** - Para empaquetar aplicaciones NestJS/Node en contenedores eficientes.
