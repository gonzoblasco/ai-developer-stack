---
name: modern-javascript-patterns
description: "Comprehensive guide for mastering modern JavaScript (ES6+) features, functional programming patterns, and best practices for writing clean, maintainable, and performant code."
risk: safe
source: community
date_added: "2026-02-27"
---

# Modern JavaScript Patterns

Practical guide for applying modern JavaScript (ES6+) features, functional programming patterns, and refactoring legacy code to be clean, maintainable, and performant.

> **Companion skill**: For conceptual reference (primitives, closures, event loop), use `javascript-mastery`. This skill focuses on **applied patterns and refactoring recipes**.

## Use this skill when

- Refactoring legacy JavaScript to modern syntax
- Implementing functional programming patterns
- Optimizing JavaScript performance
- Writing maintainable and readable code
- Working with asynchronous operations
- Building modern web applications
- Migrating from callbacks to Promises/async-await
- Implementing data transformation pipelines

## Do not use this skill when

- The task is unrelated to modern javascript patterns
- You need a different domain or tool outside this scope

---

## 1. Async Migration Patterns

### Callbacks → Promises → async/await

**Legacy (avoid)**
```javascript
function getUser(id, callback) {
  db.query(`SELECT * FROM users WHERE id = ?`, [id], (err, rows) => {
    if (err) return callback(err);
    callback(null, rows[0]);
  });
}

getUser(1, (err, user) => {
  if (err) return console.error(err);
  console.log(user);
});
```

**Promisified**
```javascript
function getUser(id) {
  return new Promise((resolve, reject) => {
    db.query(`SELECT * FROM users WHERE id = ?`, [id], (err, rows) => {
      if (err) reject(err);
      else resolve(rows[0]);
    });
  });
}
```

**Modern async/await (prefer)**
```javascript
async function getUser(id) {
  const rows = await db.query(`SELECT * FROM users WHERE id = ?`, [id]);
  return rows[0];
}

// Calling it
try {
  const user = await getUser(1);
  console.log(user);
} catch (err) {
  console.error(err);
}
```

### Parallel vs Sequential Async

```javascript
// ❌ Sequential (slow — waits for each)
const user = await fetchUser(id);
const posts = await fetchPosts(id);
const comments = await fetchComments(id);

// ✅ Parallel (fast — all run at once)
const [user, posts, comments] = await Promise.all([
  fetchUser(id),
  fetchPosts(id),
  fetchComments(id),
]);

// Controlled concurrency (avoid overwhelming the server)
async function processInBatches(items, batchSize, fn) {
  const results = [];
  for (let i = 0; i < items.length; i += batchSize) {
    const batch = items.slice(i, i + batchSize);
    const batchResults = await Promise.all(batch.map(fn));
    results.push(...batchResults);
  }
  return results;
}
```

---

## 2. Functional Programming Patterns

### Immutability Over Mutation

```javascript
// ❌ Mutating (unpredictable side effects)
function addItem(cart, item) {
  cart.items.push(item);
  cart.total += item.price;
  return cart;
}

// ✅ Immutable (predictable, testable)
function addItem(cart, item) {
  return {
    ...cart,
    items: [...cart.items, item],
    total: cart.total + item.price,
  };
}
```

### Data Transformation Pipelines

```javascript
const orders = [
  { id: 1, status: "shipped", amount: 120, customer: "Alice" },
  { id: 2, status: "pending", amount: 80, customer: "Bob" },
  { id: 3, status: "shipped", amount: 200, customer: "Alice" },
  { id: 4, status: "cancelled", amount: 50, customer: "Charlie" },
];

// Pipeline using array methods
const revenueByCustomer = orders
  .filter((order) => order.status === "shipped")
  .reduce((acc, order) => {
    acc[order.customer] = (acc[order.customer] ?? 0) + order.amount;
    return acc;
  }, {});

// { Alice: 320, Bob: 0 }
```

### Function Composition

```javascript
// compose: right-to-left
const compose = (...fns) => (x) => fns.reduceRight((v, f) => f(v), x);

// pipe: left-to-right (more readable for pipelines)
const pipe = (...fns) => (x) => fns.reduce((v, f) => f(v), x);

// Real example
const processUser = pipe(
  normalizeEmail,      // "ALICE@EXAMPLE.COM" → "alice@example.com"
  trimWhitespace,      // " Alice " → "Alice"
  sanitizeHtml,        // Remove XSS vectors
  validateSchema,      // Throws if invalid
);

const cleanUser = processUser(rawUserInput);
```

### Partial Application & Currying

```javascript
// Partial application
const multiply = (a, b) => a * b;
const double = multiply.bind(null, 2);
const triple = multiply.bind(null, 3);

double(5); // 10
triple(5); // 15

// Currying for reusable event handlers
const handleEvent = (eventType) => (handler) => (event) => {
  if (event.type === eventType) handler(event);
};

const onSubmit = handleEvent("submit")((e) => {
  e.preventDefault();
  processForm(e.target);
});

document.addEventListener("submit", onSubmit);
```

---

## 3. Object & Array Patterns

### Destructuring with Defaults

```javascript
// Safe access with defaults
function createUser({ name, role = "user", permissions = [] } = {}) {
  return { name, role, permissions };
}

// Swap without temp variable
let [a, b] = [1, 2];
[a, b] = [b, a]; // a=2, b=1

// Ignore values
const [, second, , fourth] = [1, 2, 3, 4];
```

### Dynamic Object Building

```javascript
// Build objects conditionally
function buildQuery({ search, page, limit, sort } = {}) {
  return {
    ...(search && { q: search }),
    ...(page && { page }),
    ...(limit && { per_page: limit }),
    ...(sort && { order_by: sort }),
  };
}

buildQuery({ search: "test", page: 2 });
// { q: "test", page: 2 }
```

### Optional Chaining Patterns

```javascript
// Deep nested access
const city = user?.address?.city ?? "Unknown";

// Method call that might not exist
const formatted = data?.format?.() ?? data;

// Array item access
const firstTag = post?.tags?.[0] ?? "untagged";

// Dynamic property
const value = obj?.[dynamicKey]?.nested;
```

---

## 4. Refactoring Recipes

### Replace if-else Chains with Objects/Maps

```javascript
// ❌ Long if-else chains
function getStatusLabel(status) {
  if (status === "active") return "Active";
  else if (status === "inactive") return "Inactive";
  else if (status === "pending") return "Pending";
  else return "Unknown";
}

// ✅ Lookup table
const STATUS_LABELS = {
  active: "Active",
  inactive: "Inactive",
  pending: "Pending",
};

const getStatusLabel = (status) => STATUS_LABELS[status] ?? "Unknown";
```

### Early Returns Over Deep Nesting

```javascript
// ❌ Deeply nested
function processPayment(payment) {
  if (payment) {
    if (payment.amount > 0) {
      if (payment.currency === "USD") {
        if (!payment.processed) {
          return charge(payment);
        }
      }
    }
  }
  return null;
}

// ✅ Guard clauses
function processPayment(payment) {
  if (!payment) return null;
  if (payment.amount <= 0) return null;
  if (payment.currency !== "USD") return null;
  if (payment.processed) return null;

  return charge(payment);
}
```

### Replace Magic Values with Named Constants

```javascript
// ❌ Magic numbers
if (user.role === 2) { ... }
setTimeout(sync, 86400000);

// ✅ Named constants
const USER_ROLES = { ADMIN: 1, EDITOR: 2, VIEWER: 3 };
const ONE_DAY_MS = 24 * 60 * 60 * 1000;

if (user.role === USER_ROLES.EDITOR) { ... }
setTimeout(sync, ONE_DAY_MS);
```

---

## 5. Performance Patterns

### Memoization

```javascript
function memoize(fn) {
  const cache = new Map();
  return function (...args) {
    const key = JSON.stringify(args);
    if (cache.has(key)) return cache.get(key);
    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

const expensiveCalc = memoize((n) => {
  // Expensive computation
  return fibonacci(n);
});

expensiveCalc(40); // computed
expensiveCalc(40); // cached
```

### Debounce & Throttle

```javascript
// Debounce: wait until user stops
function debounce(fn, delay) {
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}

const searchInput = debounce((query) => fetchResults(query), 300);

// Throttle: limit to once per interval
function throttle(fn, limit) {
  let inThrottle = false;
  return (...args) => {
    if (!inThrottle) {
      fn(...args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}

const onScroll = throttle(updateScrollPosition, 100);
```

### Lazy Initialization

```javascript
// Compute once, cache on object
class Config {
  get db() {
    const value = loadDatabaseConfig();
    Object.defineProperty(this, "db", { value, writable: false });
    return value;
  }
}

// Lazy module loading
async function loadHeavyFeature() {
  const { HeavyComponent } = await import("./heavy-feature.js");
  return HeavyComponent;
}
```

---

## Quick Refactoring Checklist

| Legacy Pattern | Modern Replacement |
|---|---|
| `var` | `const` / `let` |
| Callbacks | `async/await` |
| `arguments` object | Rest params `...args` |
| `Object.assign({}, x)` | Spread `{ ...x }` |
| `Array.prototype.slice.call` | `Array.from()` / spread |
| String concatenation | Template literals `` `Hello ${name}` `` |
| Prototype methods | `class` syntax |
| Sequential awaits | `Promise.all([...])` |
| `|| "default"` for all falsy | `?? "default"` for null/undefined |
| `if/else if` chains | Lookup objects / Map |

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
