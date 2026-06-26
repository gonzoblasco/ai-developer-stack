---
name: javascript-testing-patterns
description: "Comprehensive guide for implementing robust testing strategies in JavaScript/TypeScript applications using modern testing frameworks and best practices."
risk: safe
source: community
date_added: "2026-02-27"
---

# JavaScript Testing Patterns

Comprehensive guide for implementing robust testing strategies in JavaScript/TypeScript applications using modern testing frameworks and best practices.

## Use this skill when

- Setting up test infrastructure for new projects
- Writing unit tests for functions and classes
- Creating integration tests for APIs and services
- Implementing end-to-end tests for user flows
- Mocking external dependencies and APIs
- Testing React, Vue, or other frontend components
- Implementing test-driven development (TDD)
- Setting up continuous testing in CI/CD pipelines

## Do not use this skill when

- The task is unrelated to javascript testing patterns
- You need a different domain or tool outside this scope

## Instructions

- Clarify goals, constraints, and required inputs.
- Apply relevant best practices and validate outcomes.
- Provide actionable steps and verification.
- If detailed examples are required, open `resources/implementation-playbook.md`.

## Resources

- `resources/implementation-playbook.md` for detailed patterns and examples.

## Testing Pyramid

```
        E2E (few, slow, expensive)
       /     \
   Integration (moderate)
  /             \
Unit Tests (many, fast, cheap)
```

## Framework Selection

| Framework | Best For | Notes |
|-----------|----------|-------|
| **Vitest** | Unit + integration (Vite projects) | Fast, ESM-native, Jest-compatible API |
| **Jest** | Unit + integration (non-Vite) | Mature ecosystem, wide adoption |
| **Playwright** | E2E browser testing | Multi-browser, reliable, auto-waits |
| **Cypress** | E2E (simpler setup) | Great DX, real browser, good for SPAs |
| **Testing Library** | React/Vue/Angular components | Encourages accessible patterns |
| **MSW** | API mocking | Service Worker-based, realistic |

## Unit Testing

### Core Principles
- Test behavior, not implementation
- One assertion per test (ideally)
- Arrange → Act → Assert (AAA)
- Tests should be independent and deterministic

### Structure (Vitest / Jest)
```typescript
import { describe, it, expect, beforeEach, vi } from "vitest";
import { UserService } from "./user-service";

describe("UserService", () => {
  let service: UserService;

  beforeEach(() => {
    service = new UserService();
  });

  describe("getUser", () => {
    it("returns user when found", async () => {
      // Arrange
      const userId = "123";
      vi.spyOn(service, "findById").mockResolvedValue({ id: userId, name: "Alice" });

      // Act
      const result = await service.getUser(userId);

      // Assert
      expect(result).toEqual({ id: "123", name: "Alice" });
    });

    it("throws NotFoundError when user does not exist", async () => {
      vi.spyOn(service, "findById").mockResolvedValue(null);

      await expect(service.getUser("999")).rejects.toThrow("User not found");
    });
  });
});
```

### Mocking Strategies
```typescript
// Mock module
vi.mock("./email-service", () => ({
  sendEmail: vi.fn().mockResolvedValue({ success: true }),
}));

// Spy on method
const spy = vi.spyOn(obj, "method").mockReturnValue("mocked");

// Mock timer
vi.useFakeTimers();
vi.advanceTimersByTime(1000);
vi.useRealTimers();
```

## Integration Testing

### API Integration Tests
```typescript
import { describe, it, expect, beforeAll, afterAll } from "vitest";
import { createServer } from "./server";

describe("Users API", () => {
  let server: ReturnType<typeof createServer>;
  let baseUrl: string;

  beforeAll(async () => {
    server = createServer();
    await server.listen();
    baseUrl = `http://localhost:${server.port}`;
  });

  afterAll(async () => {
    await server.close();
  });

  it("GET /users/:id returns user", async () => {
    const response = await fetch(`${baseUrl}/users/1`);
    const data = await response.json();

    expect(response.status).toBe(200);
    expect(data).toMatchObject({ id: 1, name: expect.any(String) });
  });
});
```

### Database Testing
```typescript
// Use real DB in test environment (faster feedback than mocks)
beforeAll(async () => {
  await db.migrate.latest();
  await db.seed.run();
});

afterAll(async () => {
  await db.destroy();
});

afterEach(async () => {
  await db.raw("TRUNCATE TABLE users CASCADE");
});
```

## Component Testing (React)

### Testing Library Principles
- Query by role, label, text — not by CSS selectors
- Test what the user sees, not implementation details
- Avoid `getByTestId` when a semantic query is possible

```typescript
import { render, screen, userEvent } from "@testing-library/react";
import { LoginForm } from "./LoginForm";

describe("LoginForm", () => {
  it("submits credentials on form submit", async () => {
    const onSubmit = vi.fn();
    const user = userEvent.setup();

    render(<LoginForm onSubmit={onSubmit} />);

    await user.type(screen.getByLabelText("Email"), "alice@example.com");
    await user.type(screen.getByLabelText("Password"), "secret123");
    await user.click(screen.getByRole("button", { name: /sign in/i }));

    expect(onSubmit).toHaveBeenCalledWith({
      email: "alice@example.com",
      password: "secret123",
    });
  });

  it("shows error message on failed login", async () => {
    const onSubmit = vi.fn().mockRejectedValue(new Error("Invalid credentials"));
    const user = userEvent.setup();

    render(<LoginForm onSubmit={onSubmit} />);

    await user.click(screen.getByRole("button", { name: /sign in/i }));

    expect(await screen.findByText(/invalid credentials/i)).toBeInTheDocument();
  });
});
```

## API Mocking with MSW

```typescript
// handlers.ts
import { http, HttpResponse } from "msw";

export const handlers = [
  http.get("/api/users/:id", ({ params }) => {
    return HttpResponse.json({ id: params.id, name: "Alice" });
  }),

  http.post("/api/users", async ({ request }) => {
    const body = await request.json();
    return HttpResponse.json({ id: "new-id", ...body }, { status: 201 });
  }),
];

// setup.ts (Vitest)
import { setupServer } from "msw/node";
import { handlers } from "./handlers";

const server = setupServer(...handlers);

beforeAll(() => server.listen({ onUnhandledRequest: "error" }));
afterEach(() => server.resetHandlers());
afterAll(() => server.close());
```

## End-to-End Testing (Playwright)

```typescript
import { test, expect } from "@playwright/test";

test.describe("Authentication", () => {
  test("user can log in and see dashboard", async ({ page }) => {
    await page.goto("/login");

    await page.getByLabel("Email").fill("alice@example.com");
    await page.getByLabel("Password").fill("secret123");
    await page.getByRole("button", { name: "Sign In" }).click();

    await expect(page).toHaveURL("/dashboard");
    await expect(page.getByRole("heading", { name: "Dashboard" })).toBeVisible();
  });

  test("shows validation errors on empty submit", async ({ page }) => {
    await page.goto("/login");
    await page.getByRole("button", { name: "Sign In" }).click();

    await expect(page.getByText("Email is required")).toBeVisible();
  });
});
```

### Playwright Configuration
```typescript
// playwright.config.ts
import { defineConfig, devices } from "@playwright/test";

export default defineConfig({
  testDir: "./e2e",
  fullyParallel: true,
  forbidOnly: !!process.env.CI,
  retries: process.env.CI ? 2 : 0,
  workers: process.env.CI ? 1 : undefined,
  use: {
    baseURL: "http://localhost:3000",
    trace: "on-first-retry",
  },
  projects: [
    { name: "chromium", use: { ...devices["Desktop Chrome"] } },
    { name: "firefox", use: { ...devices["Desktop Firefox"] } },
  ],
  webServer: {
    command: "npm run dev",
    port: 3000,
    reuseExistingServer: !process.env.CI,
  },
});
```

## Test-Driven Development (TDD)

### Red-Green-Refactor Cycle
1. **Red** — Write a failing test
2. **Green** — Write the minimum code to pass
3. **Refactor** — Improve without breaking tests

```typescript
// 1. RED: Write test first
it("calculates tax at 10%", () => {
  expect(calculateTax(100, 0.1)).toBe(10);
});

// 2. GREEN: Minimal implementation
function calculateTax(amount: number, rate: number): number {
  return amount * rate;
}

// 3. REFACTOR: Add edge cases, improve clarity
function calculateTax(amount: number, rate: number): number {
  if (amount < 0) throw new Error("Amount cannot be negative");
  return Math.round(amount * rate * 100) / 100;
}
```

## CI/CD Integration

### GitHub Actions Example
```yaml
name: Test

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: "npm"

      - run: npm ci
      - run: npm run test:unit -- --coverage
      - run: npm run test:integration

      - name: Upload coverage
        uses: codecov/codecov-action@v4
        with:
          token: ${{ secrets.CODECOV_TOKEN }}

  e2e:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: "npm"
      - run: npm ci
      - run: npx playwright install --with-deps
      - run: npm run test:e2e
      - uses: actions/upload-artifact@v4
        if: failure()
        with:
          name: playwright-report
          path: playwright-report/
```

## Coverage Thresholds

```typescript
// vitest.config.ts
export default defineConfig({
  test: {
    coverage: {
      provider: "v8",
      reporter: ["text", "lcov", "html"],
      thresholds: {
        lines: 80,
        functions: 80,
        branches: 70,
        statements: 80,
      },
      exclude: ["**/node_modules/**", "**/dist/**", "**/*.config.*"],
    },
  },
});
```

## Test Organization Best Practices

```
src/
├── lib/
│   ├── user.ts
│   └── user.test.ts          # Co-located unit tests
├── api/
│   ├── users.ts
│   └── users.test.ts
tests/
├── integration/              # Integration tests
│   └── users-api.test.ts
└── e2e/                      # E2E tests
    └── auth.spec.ts
```

## Common Anti-Patterns to Avoid

| Anti-Pattern | Why Bad | Fix |
|---|---|---|
| Testing implementation | Brittle, breaks on refactor | Test behavior/output |
| Shared mutable state | Non-deterministic | Reset in `beforeEach` |
| Overly specific assertions | Brittle | Use `toMatchObject` |
| No test isolation | Hidden dependencies | Each test fully independent |
| Mocking everything | No real integration coverage | Use real dependencies where fast |
| Slow E2E for unit logic | Overkill | Match test type to scope |

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
