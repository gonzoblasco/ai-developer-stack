---
name: testing-patterns
description: Vitest testing patterns, factory functions, mocking strategies, and TDD workflow. Use when writing unit tests, creating test factories, or following TDD cycles.
risk: safe
source: community
date_added: "2026-06-26"
---

# Testing Patterns and Utilities (Vitest)

> **Learn to test behaviors, not implementations. Default to Vitest for modern projects.**

---

## 🧠 Testing Philosophy

- **Test-Driven Development (TDD)**: Write a failing test FIRST ➔ Implement minimal code to pass ➔ Refactor.
- **Behavior-Driven Testing**: Test what the module/component *does* (user-observable outcomes) rather than *how* it does it. Avoid testing private methods or internal state directly.
- **Factory Pattern**: Use factory functions to generate mock data or component props. This keeps tests DRY and prevents them from breaking when database schemas or API shapes change.

---

## 🧪 Mocking Patterns in Vitest

### Mocking Modules & Third-Party Libraries

Use `vi.mock()` to isolate the unit under test. Retrieve mock functions using `vi.mocked()` to obtain proper TypeScript types.

```typescript
import { vi, describe, it, expect, beforeEach } from 'vitest';
import { analytics } from './utils/analytics';
import { processPayment } from './paymentService';

// Mock the module
vi.mock('./utils/analytics', () => ({
  analytics: {
    trackEvent: vi.fn(),
  },
}));

describe('processPayment', () => {
  beforeEach(() => {
    vi.clearAllMocks();
  });

  it('tracks an analytics event on successful payment', async () => {
    await processPayment({ amount: 100 });
    
    // Type-safe verification of the mock call
    expect(vi.mocked(analytics.trackEvent)).toHaveBeenCalledWith('payment_success', { amount: 100 });
  });
});
```

### Mocking Globals & Environment Variables

```typescript
// Mocking global fetch
const mockFetch = vi.fn().mockResolvedValue({
  json: async () => ({ id: '123' }),
});
vi.stubGlobal('fetch', mockFetch);

// Mocking environment variables
vi.stubEnv('DATABASE_URL', 'postgresql://localhost:5432/test');
```

---

## 🏭 Factory Pattern (Keeping Tests Resilient)

Avoid writing inline object literals for complex models in every test. Implement factories with override capabilities:

```typescript
// factories/user.ts
export interface User {
  id: string;
  name: string;
  role: 'admin' | 'user';
  email: string;
}

export function createUserMock(overrides: Partial<User> = {}): User {
  return {
    id: 'user-default-uuid',
    name: 'Jane Doe',
    role: 'user',
    email: 'jane@example.com',
    ...overrides,
  };
}

// In your test file:
const adminUser = createUserMock({ role: 'admin' });
```

---

## 🚫 Common Anti-Patterns

| ❌ Avoid | ✅ Do |
|----------|-------|
| Mocking internal methods of the class under test | Test through the public interface/endpoints only |
| Retaining mock state between tests | Run `vi.clearAllMocks()` or `vi.restoreAllMocks()` in `beforeEach` |
| Long-running e2e tests for simple logic | Use fast unit tests; reserve e2e (Playwright) for critical user flows |
| Hardcoding database IDs in tests | Generate dynamic IDs or use factories |

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
