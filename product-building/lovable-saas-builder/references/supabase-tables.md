# Supabase Tables — Schema Típico para SaaS Multi-tenant

Schema validado en SoporteML. Adaptar según el dominio del producto.

---

## Tablas core (siempre presentes)

```sql
-- ============================================
-- 1. COMPANIES (tenant raíz)
-- ============================================
create table companies (
  id         uuid primary key default gen_random_uuid(),
  name       text not null,
  created_at timestamptz default now()
);
alter table companies enable row level security;

create policy "Users see their own company"
  on companies for select
  using (id = (select company_id from profiles where id = auth.uid()));

-- ============================================
-- 2. PROFILES (usuarios de la app)
-- Extiende auth.users de Supabase Auth
-- ============================================
create table profiles (
  id         uuid primary key references auth.users(id) on delete cascade,
  company_id uuid references companies(id),
  full_name  text,
  role       text default 'agent',  -- 'admin' | 'agent'
  created_at timestamptz default now()
);
alter table profiles enable row level security;

create policy "Users see profiles in their company"
  on profiles for select
  using (company_id = (select company_id from profiles where id = auth.uid()));

-- Auto-crear profile cuando se registra un usuario
create or replace function handle_new_user()
returns trigger as $$
begin
  insert into profiles (id) values (new.id);
  return new;
end;
$$ language plpgsql security definer;

create trigger on_auth_user_created
  after insert on auth.users
  for each row execute procedure handle_new_user();

-- ============================================
-- 3. COMPANY_SETTINGS (configuración del tenant)
-- ============================================
create table company_settings (
  id            uuid primary key default gen_random_uuid(),
  company_id    uuid references companies(id) on delete cascade unique,
  -- AI
  ai_tone       text default 'profesional',  -- 'profesional' | 'casual' | 'tecnico'
  ai_custom_instructions text,
  ai_exclusion_rules     text,
  -- Features
  auto_reply_enabled boolean default false,
  -- Timestamps
  updated_at    timestamptz default now()
);
alter table company_settings enable row level security;

create policy "Company members manage their settings"
  on company_settings for all
  using (company_id = (select company_id from profiles where id = auth.uid()));

-- ============================================
-- 4. SERVICE_TOKENS (OAuth tokens de terceros)
-- Genérico — usar para MeLi, TiendaNube, etc.
-- ============================================
create table service_tokens (
  id            uuid primary key default gen_random_uuid(),
  company_id    uuid references companies(id) on delete cascade,
  service       text not null,  -- 'mercadolibre' | 'tiendanube' | etc.
  access_token  text,
  refresh_token text,
  service_user_id text,         -- ID del usuario en el servicio externo
  expires_at    timestamptz,
  updated_at    timestamptz default now(),
  unique(company_id, service)
);
alter table service_tokens enable row level security;

-- IMPORTANTE: Los tokens se leen via Edge Functions con Service Role
-- El frontend no necesita acceder a esta tabla directamente
create policy "Company admins can see connection status"
  on service_tokens for select
  using (company_id = (select company_id from profiles where id = auth.uid()));
```

---

## Tablas de dominio (ejemplos)

```sql
-- PREGUNTAS (SoporteML)
create table questions (
  id                   uuid primary key default gen_random_uuid(),
  company_id           uuid references companies(id),
  product_id           uuid references products(id),
  external_question_id text,       -- ID en el servicio externo
  question_text        text,
  buyer_id             text,
  buyer_nickname       text,
  ai_suggested_answer  text,
  ai_category          text,
  final_answer         text,
  status               text default 'pending',  -- 'pending' | 'published' | 'discarded'
  requires_human       boolean default false,
  answered_by          uuid references auth.users(id),
  answered_at          timestamptz,
  created_at           timestamptz default now()
);
alter table questions enable row level security;

create policy "Company members manage their questions"
  on questions for all
  using (company_id = (select company_id from profiles where id = auth.uid()));
```

---

## Helper function recomendada

```sql
-- Función que retorna el company_id del usuario actual (evita subqueries repetidos)
create or replace function get_my_company_id()
returns uuid as $$
  select company_id from profiles where id = auth.uid();
$$ language sql stable security definer;

-- Uso en políticas:
-- using (company_id = get_my_company_id())
```
