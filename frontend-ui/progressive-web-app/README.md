# progressive-web-app

Skill para diseñar, estructurar e implementar Aplicaciones Web Progresivas (PWAs) con soporte sin conexión (offline), instalabilidad local y estrategias optimizadas de almacenamiento en caché.

## Resumen

Esta skill reúne los pilares obligatorios para convertir un sitio web tradicional en una aplicación instalable de apariencia nativa. Enseña a configurar el manifiesto web (`manifest.json`), registrar Service Workers (`sw.js`) con estrategias avanzadas de caché (Cache-First, Network-First, Stale-While-Revalidate) y gestionar eventos de instalación personalizados (*beforeinstallprompt*).

**Insight Clave:** El navegador no permitirá la instalación si falta una página de respaldo para navegación sin conexión (`offline.html`) precargada en el *App Shell* o si no se sirve la aplicación sobre conexiones HTTPS seguras (con excepción de localhost en desarrollo).

## Inicio Rápido

1. **Leé** [SKILL.md](SKILL.md) para comprender el flujo de registro, las peculiaridades de iOS/Safari y las estrategias de caché.
2. **Creá** tu archivo de metadatos [manifest.json](manifest.json) con íconos adaptables (*maskable*).
3. **Registrá** tu service worker en la carga inicial y captura el prompt de instalación personalizado en tu archivo de script principal (`app.js`).
4. **Validá** que tu service worker administre la memoria caché correctamente y prueba la carga sin conexión usando la pestaña de depuración "Network" (simulando "Offline") en las DevTools del navegador.

## Qué Incluye

### Documentación Core

- **[SKILL.md](SKILL.md)** - Estructura de manifiestos, shell HTML con soporte para Safari, registro de Service Worker, implementaciones de estrategias de caché y andamio con Workbox.

## Estrategias de Caché Clave

*   **Cache-First (Activos Estáticos):** Carga desde la caché instantáneamente y solo consulta a la red si el recurso (CSS, JS, imágenes) no está guardado.
*   **Network-First (Páginas HTML):** Prioriza la frescura del contenido consultando a la red. Si el usuario no tiene conexión, cae al HTML en caché o a la página `offline.html` de respaldo.
*   **Stale-While-Revalidate (APIs):** Devuelve la información de la caché de inmediato para máxima velocidad y, en segundo plano, realiza una petición de red para actualizar la caché.

## Estructura

```
progressive-web-app/
└── SKILL.md                  # Contenido de configuración PWA
```

## Skills Relacionadas

- **`frontend-developer`** - Para integrar el soporte sin conexión con la lógica de componentes React/Next.js.
- **`web-design-guidelines`** - Para garantizar que los layouts se comporten correctamente en modo standalone (sin barras de navegador).
