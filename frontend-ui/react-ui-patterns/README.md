# React UI Patterns

Guía de patrones de interfaz de usuario modernos en React para manejar estados de carga (loading), manejo de errores y estados vacíos (empty states).

## Resumen

Esta habilidad define principios fundamentales y estructuras reutilizables para garantizar que la interfaz de usuario de React sea responsiva, no oculte errores al usuario y evite parpadeos (flashing) de elementos de carga innecesarios.

## Inicio Rápido

Para implementar un estado de carga y error robusto al renderizar listas de datos:

```typescript
const { data, loading, error, refetch } = useGetItemsQuery();

if (error) return <ErrorState error={error} onRetry={refetch} />;
// Mostrar esqueleto/spinner de carga únicamente si estamos cargando y NO hay datos en caché
if (loading && !data) return <LoadingSkeleton />;
if (!data?.items.length) return <EmptyState title="No hay elementos" />;

return <ItemList items={data.items} />;
```

## Qué Incluye

- **Regla de Carga (The Golden Rule)**: Criterios para alternar entre Skeletons, Spinners y renderizado del contenido caché.
- **Jerarquía de Manejo de Errores**: Estrategias de retroalimentación visual (Validaciones inline, Toasts, Banners de error, y pantallas de error a pantalla completa).
- **Control de Estados en Botones**: Prevención de múltiples clics inhabilitando botones (`disabled`) y mostrando animaciones de carga (`isLoading`).
- **Estados Vacíos Contextuales**: Requisitos y estructuras de componentes para listas vacías o búsquedas sin resultados.
- **Lista de Verificación de UI**: Guía de autoevaluación antes de finalizar cualquier componente.

## Conceptos Clave

- **No mostrar UI obsoleta ni parpadeos**: No reemplazar datos ya cacheados con spinners a mitad de un refetch.
- **No silenciar errores**: Asegurarse de que cada flujo asíncrono o mutación tenga un manejador `onError` que reporte el problema.
- **Degradación progresiva y actualizaciones optimistas**: Dar prioridad a mostrar datos parciales y actualizar la UI de inmediato en lugar de esperar la respuesta del servidor.

## Estructura de la Habilidad

```
react-ui-patterns/
├── SKILL.md                 # Guía principal con las reglas y anti-patrones
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [react-best-practices](../react-best-practices/README.md) - Estándares de calidad de React.
- [react-state-management](../react-state-management/README.md) - Flujo y store de datos en React.
- [testing-patterns](../../languages-standards/testing-patterns/README.md) - Pruebas para verificar estados límite (loading, empty, error).
