---
name: pr
description: Crear un pull request para la branch actual con descripción estructurada, correr el review, y mergear cuando el review apruebe.
risk: unknown
source: community
date_added: "2026-06-26"
---

# pr

## Propósito

Crear un pull request para la branch actual con descripción estructurada, correr el review,
y mergear cuando el review apruebe. Es el cierre formal de cada task.

## Precondiciones

- `npm run build` debe pasar sin errores antes de crear el PR
- Todos los cambios commiteados (`git status` limpio)
- La branch pusheada a origin

## Invocación

```
/pr
```

---

## Pasos

**1. Verificar que el build pasa**

```bash
npm run build
```

Si falla: corregir antes de continuar. No crear PRs con builds rotos.

**2. Commitear cambios pendientes**

```bash
git status
# Si hay cambios sin commitear: usar /commit antes de continuar
```

**3. Pushear la branch**

```bash
git push -u origin $(git branch --show-current)
```

**4. Obtener el token de GitHub**

```bash
GITHUB_TOKEN=$(grep GITHUB_TOKEN .env.local | cut -d= -f2)
```

**5. Crear el PR via API de GitHub**

```bash
curl -s -X POST \
  -H "Authorization: token $GITHUB_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/repos/[OWNER]/[REPO]/pulls \
  -d '{
    "title": "feat(scope): descripción",
    "head": "'"$(git branch --show-current)"'",
    "base": "main",
    "body": "..."
  }'
```

Reemplazar `[OWNER]` y `[REPO]` por los valores correctos.

**6. Correr el review**

```bash
git diff main...HEAD
```

Aplicar el skill `/review` (o el equivalente de este proyecto si existe).
Si encuentra bloqueantes: corregir → `/commit` → `git push` → repetir.

**7. Mergear cuando el review apruebe**

```bash
curl -s -X PUT \
  -H "Authorization: token $GITHUB_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/repos/[OWNER]/[REPO]/pulls/{{PR_NUMBER}}/merge \
  -d '{"merge_method": "merge"}'
```

Reemplazar `[OWNER]`, `[REPO]` y `{{PR_NUMBER}}` con los valores correctos.

Método siempre `merge` — nunca `squash`. Esto preserva el historial individual de cada task.

**8. Volver a main y actualizar**

```bash
git checkout main
git pull origin main
```

No eliminar la branch — sirve como referencia histórica.

---

## Plantilla del body del PR

```markdown
## ¿Qué hace este PR?
<!-- Una o dos oraciones describiendo el cambio desde la perspectiva del producto o arquitectura. -->

## Cambios técnicos principales
<!-- Listar los archivos o componentes nuevos/modificados. 2-4 bullets max. -->
- 
- 

## Cómo testear
<!-- Pasos para verificar que el cambio funciona. Importante si es backend o lógica compleja. -->
1. 
2. 

## Checklist
- [ ] `npm run build` pasa sin errores
- [ ] `npm run dev` funciona — probado manualmente el flujo principal
- [ ] No hay console.logs de debug
- [ ] No hay secrets hardcodeados
- [ ] No hay credenciales o datos sensibles en la descripción
- [ ] El review (`/review` o equivalente) no encontró bloqueantes
- [ ] Si hay UI: los estados vacío y error están manejados

## Screenshots (si aplica)
<!-- Si es un cambio visual, adjuntar screenshot antes/después. -->
```

---

## Scopes válidos para el título del PR

{{FILL: Listar los scopes de este proyecto.

Convención: Los scopes deben coincidir con los de `/commit`.
Ejemplo para un e-commerce: auth, catalog, cart, payments, admin, db, notifications

El título del PR siempre debe seguir Conventional Commits:
`<tipo>(<scope>): descripción`

Ejemplos:
- `feat(cart): add quantity selector`
- `fix(auth): prevent login bypass on expired session`
- `refactor(db): consolidate migration scripts`
- `chore: update dependencies`
}}

---

## Validación del PR

Un PR está bien formado si:
- El título sigue Conventional Commits: `<tipo>(<scope>): descripción`
- El body es claro y conciso (no párrafos largos sin formato)
- El checklist está marcado (al menos que `npm run build` pasó)
- La descripción del qué es breve; el cómo está en el diff

## Modos de falla comunes

**Crear PR sin que pasen los tests locales.** Si `npm run build` falla en tu máquina, también
fallará en CI. No esperes a que lo encuentre el reviewer.

**PRs con múltiples responsabilidades mezcladas.** Una tarea = un PR. Si cambiaste auth y
también la UI del carrito, son dos PRs diferentes. El historial sufre si se mezclan.

**Body vacío.** El template existe por una razón. Completarlo toma 2 minutos y le ahorra
tiempo al reviewer. El body es comunicación asincrónica con el equipo.

**Olvidar pushear la branch.** Si `git push -u` no se ejecuta o falla, el PR va a estar
apuntando a una rama que no existe en origin. Verificar siempre con `git branch -vv`.
