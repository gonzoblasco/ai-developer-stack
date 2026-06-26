# Production QA Validator

Habilidad de aseguramiento de calidad (QA) y auditoría de lanzamiento para aplicaciones Fullstack basadas en Next.js. Proporciona un conjunto de herramientas y funciones shell estructuradas en 13 fases.

## Resumen

Esta habilidad ayuda a certificar que una aplicación Next.js está lista para desplegarse en producción sin incidentes. Automatiza pruebas de tipado e imports, evalúa el renderizado de páginas dinámicas vs estáticas, audita cookies de sesión, comprueba la correcta carga de metadatos SEO, analiza el peso del bundle JS, valida la seguridad de base de datos (inyección SQL) y previene la fuga de secretos (credentials/tokens).

## Inicio Rápido

Para ejecutar el set de validaciones rápidas, define la URL de producción y corre las funciones consolidadas en tu shell:

```bash
export PROD_URL="https://midominio.com"

# Ejecutar pruebas básicas (código, compilación, rutas principales, SEO, git y humo)
qa:all

# Ejecutar pruebas avanzadas completas (auth, cookies, lazyload, vulnerabilidades y limpieza)
qa:full
```

## Qué Incluye

### Las 13 Fases de Validación
1. **Code Integrity**: Verificación de tipos (`tsc`), formateo de sintaxis (`eslint`) y pruebas unitarias.
2. **Build Verification**: Análisis estático del output de compilación (`npm run build`) para verificar páginas estáticas (`○`/`●`) y dinámicas (`λ`).
3. **Session & Authentication**: Comprobación de seguridad en cookies de sesión (HttpOnly, Secure, SameSite) y protección de rutas.
4. **Route Regression**: Verificación de códigos de respuesta en sitemap, robots.txt y rutas críticas.
5. **SEO & Metadata**: Auditoría de etiquetas descriptivas, canonicals, favicons, y dimensiones de imágenes Open Graph (og:image ≥ 1200x630px).
6. **API Route Behavior**: Tiempos de respuesta de endpoints API y normalización en la estructura de errores JSON.
7. **Git Hygiene**: Detección de credenciales quemadas en el diff de Git e inclusión de archivos del compilador en el `.gitignore`.
8. **Smoke Test**: Validación posterior al despliegue para asegurar que la app responda correctamente en la nube.
9. **Page Speed & Bundles**: Análisis preliminar de carga diferida (lazy load) y control de peso total de página (<1MB).
10. **Cleanup & Vulnerability Scan**: Auditoría de seguridad del gestor de paquetes (`npm audit`) y remoción de console.logs.
11. **UI/UX & Error Boundaries**: Aseguramiento de accesibilidad móvil (touch targets ≥ 44x44px), animaciones eficientes y límites de error (`app/error.tsx`).
12. **Database & Data Layer**: Verificación de N+1 queries, URLs de bases de datos quemadas y sincronización de migraciones.
13. **Secure Data Rendering**: Prevención de vulnerabilidades XSS (`dangerouslySetInnerHTML`), ocultación de correos en la UI y prevención de fugas de stack traces en errores API.

## Conceptos Clave

- **Ejecución Secuencial**: No avanzar a fases avanzadas (como testing de rendimiento) si las previas (como compilación del código e integridad de tipos) fallan.
- **Validación Práctica**: Emplear comandos del sistema integrados (ej: `curl`, `identify` de imagemagick) para automatizar la revisión.

## Estructura de la Habilidad

```
vibecode-production-qa-validator/
├── SKILL.md                 # Definición de funciones y scripts de verificación de las 13 fases
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [react-nextjs-development](../react-nextjs-development/README.md) - Fases y andamiaje del flujo de desarrollo.
- [vibe-code-auditor](../vibe-code-auditor/README.md) - Auditorías del código para evaluar deuda técnica de MVPs.
- [vibe-code-cleanup](../../fullstack/vibe-code-cleanup/README.md) - Limpieza y refactorización previa de base de código.
