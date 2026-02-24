# Lovable Tips — Límites, Trucos y Errores Comunes

Aprendizajes del mundo real. Cada punto acá costó tiempo descubrirlo.

---

## 🟢 Lo que funciona bien

### Prompts acotados y específicos

Un prompt por feature, con datos claros del schema. Lovable responde mucho mejor cuando sabe exactamente qué tabla leer y qué campos mostrar.

### "Use mock data first"

Pedirle que genere UI con data mockeada y después conectar Supabase acelera enormemente la iteración visual.

### Iterar sobre lo que generó

"Modify the Inbox page to also show X" funciona mejor que reescribir todo. Lovable tiene buena memoria dentro del mismo chat.

### Edge Functions en chats separados

Crear cada Edge Function en un chat nuevo evita que el contexto se mezcle con el código del frontend.

---

## 🔴 Errores comunes y cómo evitarlos

### ❌ "Delete the existing component and replace it with..."

**Problema**: Lovable a veces borra más de lo pedido o pierde commits anteriores.
**Solución**: Decir siempre "Modify", "Update", "Add to" en vez de "Delete" o "Replace".

### ❌ Agregar muchos features en un solo prompt

**Problema**: El código generado es inconsistente, mezcla estilos y rompe features anteriores.
**Solución**: Un feature por prompt. Si el prompt tiene más de 3 secciones (\*\*), dividirlo.

### ❌ No verificar el preview antes de continuar

**Problema**: Lovable puede generar código que compila pero tiene errores visuales o lógicos silenciosos.
**Solución**: Abrir el preview de Lovable después de cada prompt y verificar manualmente.

### ❌ Asumir que el schema de Supabase ya está

**Problema**: Si las tablas no existen cuando Lovable intenta conectarse, la app crashea silenciosamente.
**Solución**: Siempre crear las tablas en Supabase antes de pedirle a Lovable que las consuma.

### ❌ Variables de entorno sin configurar

**Problema**: La Edge Function usa `Deno.env.get("MI_KEY")` pero la variable no existe → la función retorna errores silenciosos.
**Solución**: Antes de probar cualquier Edge Function, verificar que las secrets estén en el panel de Supabase.

---

## 🟡 Tips de productividad

### Nombrar las Edge Functions con verbos

Patrón: `[verbo]-[servicio]-[recurso]`

- ✅ `sync-meli-questions`, `publish-meli-answer`, `disconnect-meli`
- ❌ `questions`, `meli`, `function1`

### Siempre `console.log()` en Edge Functions

Lovable Cloud muestra los logs en tiempo real en el panel de Supabase. Loggear el inicio, los parámetros de entrada, y el resultado de cada operación crítica.

### Forzar modo oscuro desde el inicio

Si el diseño es dark mode, declararlo desde el `<html>` tag:

```html
<html class="dark"></html>
```

O en `index.css`:

```css
:root {
  color-scheme: dark;
}
```

Cambiarlo después requiere revisar decenas de componentes.

### El chat después de ~15 mensajes pierde contexto

Lovable tiene ventana de contexto limitada. Cuando el chat está largo:

1. Abrir un chat nuevo
2. Empezar con: "Continue building [App Name]. The current state is: [descripción del estado actual]. Now I need to..."

### Conectar el repositorio de GitHub

Lovable Cloud permite conectar un repo de GitHub para hacer push de los cambios. Hacerlo desde el inicio evita perder código si hay problemas con el proyecto.

---

## 🔵 Acerca del AI Gateway de Lovable

- La variable `LOVABLE_API_KEY` está disponible automáticamente en todas las Edge Functions
- El modelo recomendado es `google/gemini-2.5-flash` (el más rápido y económico)
- Las respuestas del AI Gateway a veces incluyen texto antes/después del JSON → siempre usar regex para extraer: `content.match(/\{[\s\S]*\}/)`
- El límite de tokens por respuesta puede crecer si el `systemPrompt` es muy largo

---

## 🔧 Cuando algo no funciona

Orden de debugging recomendado:

1. **¿Compila sin errores?** → Ver la consola del navegador en el preview
2. **¿La Edge Function responde?** → Ver logs en Supabase → Edge Functions → Logs
3. **¿Las políticas RLS están bloqueando?** → En Supabase, deshabilitar temporalmente RLS para confirmar
4. **¿Las variables de entorno están bien?** → Agregar un `console.log()` al inicio de la Edge Function con `Object.keys(Deno.env.toObject())`
5. **¿El schema de la tabla cambió?** → Comparar los tipos del schema con lo que el código espera
