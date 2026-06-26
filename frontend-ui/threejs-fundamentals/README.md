# Three.js Fundamentals

Guía y patrones de desarrollo esenciales para configurar escenas, cámaras, renderizadores, transformaciones y jerarquías tridimensionales utilizando Three.js.

## Resumen

Esta habilidad proporciona el andamiaje básico y las mejores prácticas para inicializar escenas 3D interactivas en la web. Cubre la creación de renderizadores (`WebGLRenderer` y el moderno `WebGPURenderer`), cámaras perspectiva u ortográficas, el sistema de coordenadas de mano derecha, transformaciones de objetos, optimización de memoria y utilidades matemáticas tridimensionales.

## Inicio Rápido

Para inicializar una escena 3D básica con un renderizador responsivo:

```javascript
import * as THREE from 'three';

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer({ antialias: true });

renderer.setSize(window.innerWidth, window.innerHeight);
renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
document.body.appendChild(renderer.domElement);

const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshStandardMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

camera.position.z = 5;

// Loop de animación optimizado
renderer.setAnimationLoop(() => {
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;
  renderer.render(scene, camera);
});

// Manejo de responsividad
window.addEventListener('resize', () => {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});
```

## Qué Incluye

- **Configuración de Escena y Cámaras**: Parámetros de `PerspectiveCamera`, `OrthographicCamera`, y técnicas avanzadas como `CubeCamera` para reflejos en tiempo real.
- **Configuración del WebGLRenderer**: Activación de sombras (`shadowMap`), mapeo de tonos (Tone Mapping), perfiles de color (SRGB) y rendimiento de GPU.
- **Sistema de Coordenadas de Mano Derecha**: Orientación espacial tridimensional (+X derecha, +Y arriba, +Z hacia el observador) y su visualización con `AxesHelper`.
- **Estructura de Object3D y Grupos**: Relaciones parent-child, transformaciones (rotaciones con Eulers y Cuaterniones), y propagación de matrices.
- **Limpieza de Recursos (Memory Cleanup)**: Liberación explícita de geometrías, materiales y texturas mediante el método `.dispose()`.
- **Soporte Experimental WebGPU**: Renderizador basado en WebGPU disponible en versiones recientes (r183+).

## Conceptos Clave

- **Frecuencia de Actualización vs Rendimiento**: Uso recomendado de `renderer.setAnimationLoop` en lugar de `requestAnimationFrame` manual para compatibilidad con WebXR.
- **Disposición de Recursos**: Prevenir fugas de memoria (memory leaks) llamando a `.dispose()` de forma recursiva al eliminar objetos o desmontar vistas en la UI.
- **Optimización de Draw Calls**: Agrupación de geometrías estáticas e instanciación de mallas para maximizar la tasa de frames por segundo (FPS).

## Estructura de la Habilidad

```
threejs-fundamentals/
├── SKILL.md                 # Guía técnica fundamental y clases core
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [web-design-guidelines](../web-design-guidelines/README.md) - Principios de diseño visual y layouts interactivos.
- [frontend-dev-guidelines](../frontend-dev-guidelines/README.md) - Pautas generales de desarrollo en frontend.
