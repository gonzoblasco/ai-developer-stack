---
name: UI Review (Next.js + Tailwind)
description: Review UI changes for common issues (Server vs Client components, layout, responsiveness, a11y, semantics, Tailwind best practices) and output a prioritized QA checklist + minimal fixes.
---

# Skill: UI Review (Next.js App Router + Tailwind CSS)

## Goal

Perform a comprehensive UI and code review for a Next.js (App Router) feature styled with Tailwind CSS. Your objective is to identify bugs, UX/Accessibility (A11y) issues, Next.js anti-patterns, and Tailwind CSS maintainability problems. Produce a practical, prioritized QA report along with minimal, safe fixes.

## Inputs

- Target route(s) or component(s) to review (e.g., `/about` or `components/InfoCard.tsx`).
- Changed files (if provided via a git diff or explicit list).
- Any specific acceptance criteria provided by the user.

## Outputs (Must Produce)

1. **QA Checklist**: A list of manual testing steps to verify the UI.
2. **Prioritized Findings**: Grouped by severity:
   - **P0 (Critical)**: Broken behavior, runtime errors, Next.js hydration mismatches, layout totally broken on mobile/desktop.
   - **P1 (UX / Accessibility)**: Poor contrast, missing focus states, unclickable areas, missing ARIA attributes where essential, image optimization issues.
   - **P2 (Maintainability / Polish)**: Tailwind "class soup", unnecessary `"use client"` directives, hardcoded values instead of theme tokens, missing semantic HTML.
3. **Minimal Fix Plan**: Concrete, minimal code changes to address the findings. Only provide fixes necessary to meet best practices.
4. **Verification**: Clear commands or steps to verify the fixes (e.g., `npm run dev` and visual checks).

## Review Dimensions & Best Practices

When reviewing the code, explicitly check for the following:

### 1. Next.js App Router Specifics

- **Server vs. Client Components**: Components should default to Server Components. The `"use client"` directive should only be used at the "leaves" of the component tree (e.g., components needing `useState`, `useEffect`, event listeners, or browser APIs).
- **Data Fetching**: Ensure data is fetched directly within Server Components (`async`/`await`) where possible, avoiding unnecessary client-side fetching waterfalls.
- **Optimized Assets**: Check for the usage of `next/image` (`<Image />`) for images and `next/link` (`<Link>`) for internal navigation.
- **Loading & Error States**: Verify the presence of `loading.tsx` and `error.tsx` handling for robust UX.

### 2. Tailwind CSS Hygiene & Maintainability

- **Avoid "Class Soup"**: If a complex combination of utility classes and DOM structure is repeated, it should be extracted into a reusable React component.
- **Mobile-First Responsiveness**: Ensure base classes apply to mobile, using responsive prefixes (`sm:`, `md:`, `lg:`, `xl:`) to enhance for larger screens. Check that layouts stack on mobile and use grids/flexbox appropriately on desktop.
- **Avoid Arbitrary Values**: Flag the use of hardcoded arbitrary values (e.g., `w-[325px]`, `p-[14px]`) when existing theme scale values (e.g., `w-80`, `p-4`) could be used.
- **`@apply` Directive**: Discourage heavy use of `@apply` in CSS files unless absolutely necessary (e.g., third-party library overrides). Favor component abstraction instead.

### 3. Accessibility (A11y) & UX

- **Keyboard Navigation**: Interactive elements must have visible focus states (e.g., `focus-visible:ring`, `focus-visible:outline`). Ensure `tabindex` is used correctly (if at all).
- **Color Contrast**: Best-effort assessment of text contrast against its background.
- **Semantic HTML**: Ensure the use of landmark tags (`<main>`, `<nav>`, `<aside>`, `<header>`, `<footer>`) and appropriate structurally semantic tags (`<article>`, `<section>`, `<ul>`/`<li>`). Use `<button>` for actions and `<a>` for navigation.
- **Heading Order**: Verify a logical heading hierarchy (only one `<h1>` per page, followed sequentially by `<h2>`, `<h3>`, etc.).
- **Screen Readers**: Check for appropriate `alt` text on images and `aria-label` or `aria-hidden` attributes on icon-only buttons or decorative elements.

### 4. Correctness & Consistency

- Renders without errors and meets all stated acceptance criteria.
- Consistency with existing repository patterns (e.g., `components/ui/`, naming conventions, file structure).

## Procedure

1. Read the target page/component source code.
2. Analyze the component architecture (Client vs. Server) and asset usage (Next.js specific components).
3. Inspect Tailwind classes for responsiveness, layout logic, and maintainability.
4. Evaluate semantic HTML and accessibility features.
5. Generate the QA Checklist, Findings, Fix Plan, and Verification steps.
6. **NEVER refactor broadly**: Recommend minimal, localized fixes to address the specific findings.

## Strict Anti-patterns (Do Not Do)

- **Do not invent browser screenshots or runtime output.**
- **Do not propose massive architectural redesigns** unless the current state is fundamentally broken (e.g., putting `"use client"` on the root layout).
- **Do not blindly apply `@apply`** to clean up classes; suggest creating a discrete React component instead.
