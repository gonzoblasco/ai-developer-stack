# TanStack Query Expert

Guía de referencia y mejores prácticas para el manejo de estado asíncrono y sincronización de datos con el servidor utilizando TanStack Query (React Query) en aplicaciones React y Next.js.

## Resumen

Esta habilidad abarca desde conceptos fundamentales de almacenamiento en caché y deduplicación de peticiones, hasta patrones avanzados de invalidación, actualizaciones optimistas de la interfaz (Optimistic Updates) e hidratación en arquitecturas híbridas de renderizado en servidor (SSR) como Next.js App Router.

## Inicio Rápido

Para implementar una consulta básica encapsulada en un Custom Hook:

```typescript
import { useQuery } from '@tanstack/react-query';

const fetchUser = async (userId: string) => {
  const res = await fetch(`/api/users/${userId}`);
  if (!res.ok) throw new Error('Error al cargar usuario');
  return res.json();
};

export const useUser = (userId: string) => {
  return useQuery({
    queryKey: ['users', userId],
    queryFn: () => fetchUser(userId),
    staleTime: 1000 * 60 * 5, // Fresco durante 5 minutos
    enabled: !!userId,        // Query dependiente
  });
};
```

## Qué Incluye

- **Deduplicación y Caching**: Explicación de ciclos de vida de caché y diferencias entre `staleTime` (refrescos en segundo plano) y `gcTime` (limpieza de memoria).
- **Factorías de Query Keys**: Organización estructurada de identificadores de caché para evitar tipados incorrectos.
- **Mutaciones**: Patrón `useMutation` básico con invalidación explícita (`invalidateQueries`).
- **Optimistic Updates**: Manejo de cambios locales instantáneos con guardado de estado de respaldo (rollback) y sincronización posterior.
- **Integración con Next.js App Router**: Configuración del proveedor del cliente e hidratación desde Server Components mediante `<HydrationBoundary>`.

## Conceptos Clave

- **Estado Asíncrono frente a Estado Local**: TanStack Query no es un cliente de fetch, es un manejador de estado. Evita copiar datos de queries a estados locales de React (`useState` / `useEffect`).
- **Deduplicación Automática**: Evita llamadas simultáneas redundantes al backend para un mismo recurso.
- **Consultas Dependientes**: Controlar la ejecución condicional mediante la propiedad `enabled`.

## Estructura de la Habilidad

```
tanstack-query-expert/
├── SKILL.md                 # Guía técnica e integraciones de React Query
└── README.md                # Esta guía de referencia y documentación
```

## Skills Relacionadas

- [react-state-management](../react-state-management/README.md) - Contexto de stores globales y locales.
- [nextjs-best-practices](../nextjs-best-practices/README.md) - Buenas prácticas del lado del servidor en Next.js.
- [react-ui-patterns](../react-ui-patterns/README.md) - Control visual de cargas y manejadores de error.
