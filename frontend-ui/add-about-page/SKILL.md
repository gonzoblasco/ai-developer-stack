---
name: add-about-page
description: Use cuando el usuario pida agregar una página About o una feature /about en Next.js (App Router). Keywords: about page, add page, InfoCard, next.js.
---

# Skill: Add About Page (Next.js App Router)

## Overview

This skill provides a bulletproof guide for creating a standard, responsive `/about` page with exactly two `InfoCard` components in a Next.js App Router application. It enforces strict constraints to prevent hallucinated components or layouts.

## Goal

Add a new `/about` page (App Router) that renders a title and **exactly 2** `InfoCard` components in a responsive grid.

## Context & Preconditions

- The repository uses Next.js with the **App Router** (`src/app/` or `app/` exists).
- Tailwind CSS is available (or use the existing styling approach in the repo).

## Inputs

- Title text (default: "About Us")
- Card A title + description
- Card B title + description

## Output Artifacts

- `app/about/page.tsx` or `src/app/about/page.tsx` created or updated.
- `components/InfoCard.tsx` (or the repository’s standard component path) created or updated.
- Final Verification block (commands + UI checklist).

## Procedure (Step-by-Step)

1. **Detect App Directory**: Check if `src/app` exists (preferred). If not, use `app`.
2. **Implementation Plan & Task List**: Produce an `implementation_plan.md` and a `task.md` with explicit acceptance criteria.
3. **Implement Component**: Create or update the `InfoCard` component (typically with a title, description, and optional icon/children if patterns exist in the repo).
4. **Implement Page**: Create the `/about` page using exactly 2 instances of `InfoCard`.
5. **Responsive Layout**: Ensure the layout is 1 column on mobile and 2 columns on desktop (use CSS grid or flexbox).
6. **Verification Steps**: Provide clear verification commands (e.g., `npm run dev`) and a UI checklist for manual testing.

## Strict Anti-Patterns (Do NOT Do)

- **Do not invent execution output** or browser screenshots.
- **Do not create extra cards**, placeholders, or sample lists beyond the **exactly 2** cards requested.
- **Do not refactor unrelated files** or perform massive architectural changes.

## Quality Affirmation (Acceptance Criteria)

- Visiting `/about` works without any runtime errors or hydration mismatches.
- The page renders a main title and **exactly 2** `InfoCard` components.
- The layout is correctly responsive: stacked (1 column) on small screens, side-by-side (2 columns) on wide screens.
- All styling follows a mobile-first approach.
