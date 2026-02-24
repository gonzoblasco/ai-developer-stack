# Paso 3: Supabase Schema — La Base de Datos

## Estructura multi-tenant recomendada

La mayoría de SaaS B2B siguen un esquema multi-tenant donde **una empresa** tiene **muchos usuarios** y **muchos datos**. Este es el patrón validado en SoporteML:

```
companies (empresa/organización)
  └── profiles (usuarios de esa empresa, linked to auth.users)
  └── [cualquier entidad de negocio] (questions, products, tickets, etc.)
```

## Tablas base que casi siempre necesitás

```sql
-- 1. companies: la unidad de negocio (tenant)
create table companies (
  id uuid primary key default gen_random_uuid(),
  name text not null,
  created_at timestamptz default now()
);

-- 2. profiles: usuarios de la app (extiende auth.users de Supabase)
create table profiles (
  id uuid primary key references auth.users(id) on delete cascade,
  company_id uuid references companies(id),
  full_name text,
  role text default 'agent', -- 'admin', 'agent', etc.
  created_at timestamptz default now()
);

-- 3. [ejemplo] tokens de terceros (OAuth de MeLi, TiendaNube, etc.)
create table service_tokens (
  id uuid primary key default gen_random_uuid(),
  company_id uuid references companies(id) on delete cascade,
  service text not null, -- 'mercadolibre', 'tiendanube', etc.
  access_token text,
  refresh_token text,
  expires_at timestamptz,
  updated_at timestamptz default now(),
  unique(company_id, service)
);
```

## Row Level Security (RLS) — Obligatorio

> [!IMPORTANT]
> Activar RLS en TODAS las tablas antes de exponer datos al frontend. Sin RLS, cualquier usuario autenticado puede ver datos de otras empresas.

### Patrón de política estándar

```sql
-- Activar RLS
alter table companies enable row level security;
alter table profiles enable row level security;

-- Política: usuario solo ve su propia empresa
create policy "Users can view their own company"
  on companies for select
  using (id = (select company_id from profiles where id = auth.uid()));

-- Política: usuario solo ve perfiles de su empresa
create policy "Users can view profiles in their company"
  on profiles for select
  using (company_id = (select company_id from profiles where id = auth.uid()));
```

## Cómo pedirle el schema a Lovable

```
Now set up the Supabase database schema. I need these tables:
[lista tus tablas]

For each table, create:
1. The SQL migration
2. Enable RLS
3. The basic read/write policies so users can only access data from their own company

Use the pattern: users belong to a company via the `profiles` table (which references auth.users).
```

## Verificación

En Lovable Cloud podés ver el schema en el panel de Supabase integrado. Verificá:

- [ ] Todas las tablas tienen `company_id` (excepto `companies`)
- [ ] RLS está activado (verde) en todas las tablas
- [ ] Existe al menos una política de SELECT por tabla
