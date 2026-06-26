# nextjs-production-debugger

Guía de diagnóstico y supervivencia para resolver problemas críticos de producción en aplicaciones Next.js (App Router), incluyendo discordancias de hidratación, discrepancias SSR/CSR, desajustes de runtime y problemas de caché.

## Resumen

Esta skill proporciona diagnósticos paso a paso para solucionar fallas en entornos de producción. Cubre el aislamiento de bugs del lado del servidor frente a los del cliente, la depuración y mitigación de errores de hidratación (*Uncanny Valley*), limitaciones del Edge Runtime frente a Node.js, optimizaciones de carga (cascadas de peticiones, bloqueo de renderizado) y la gestión del ciclo de vida del caché.

**Insight Clave:** La mayoría de los errores de hidratación ocurren por el uso de valores no deterministas (como timestamps dinámicos o números aleatorios) directamente en el cuerpo del render, o por HTML semánticamente inválido (como divs dentro de etiquetas p) que el navegador intenta auto-corregir provocando discrepancias con el servidor.

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para familiarizarte con las tablas de escenarios de depuración y capas de caché.
2. **Identificá** si el bug pertenece a SSR (deshabilitando JavaScript para ver el HTML crudo) o a CSR (inspeccionando la consola de desarrollo del navegador).
3. **Solucioná** errores de hidratación moviendo lógica dependiente de variables del cliente (`window`, fechas) a bloques `useEffect` o configurando `suppressHydrationWarning`.
4. **Analizá** el tipo de compilación localmente ejecutando:
   ```bash
   npm run build
   ```
   E identifica si las rutas problemáticas se están compilando como Estáticas (O) o Dinámicas (ƒ).

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Diagnósticos rápidos para:
  1. Aislamiento de bugs SSR vs CSR.
  2. Depuración de Hydration Errors.
  3. Desajustes en Edge vs Node Runtime (módulos como `fs` en el Middleware).
  4. Optimización de cascadas (waterfalls) y Streaming SSR.
  5. Troubleshooting de capas de caché (Data Cache, Full Route Cache, Router Cache).

## Pautas de Depuración Destacadas

*   **Evitar Bloqueos en SSR:** Envolver componentes lentos de servidor en etiquetas `<Suspense>` con loaders tipo Skeleton para forzar el streaming de datos en lugar de bloquear la entrega del HTML completo.
*   **Gestión del Caché:** Uso correcto de `revalidatePath` en Server Actions para purgar el Router Cache del cliente, y uso de `no-store` o `force-dynamic` para inhabilitar el caché de datos en tiempo real.

## Estructura

```
nextjs-production-debugger/
└── SKILL.md                  # Pautas de debugging en Next.js
```

## Skills Relacionadas

- **`nextjs-best-practices`** - Para conocer la estructura correcta y las pautas generales de diseño en Next.js.
- **`ui-review-nextjs-tailwind`** - Para revisar código y alineación de estilos antes de desplegar en producción.
