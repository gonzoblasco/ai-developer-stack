---
name: accessibility-audit
description: "Conduct comprehensive web accessibility audits for WCAG compliance, keyboard navigation, screen reader compatibility, and color contrast."
risk: safe
source: community
date_added: "2026-06-26"
---

# Accessibility Audit and Testing

Conduct comprehensive accessibility audits, identify barriers, provide remediation guidance, and ensure digital products are accessible to all users in compliance with WCAG standards.

---

## 🔍 Core Audit Areas

### 1. Keyboard Navigation
- **Focus Indicators**: Every interactive element (buttons, links, inputs) must have a highly visible focus ring when focused via keyboard navigation.
- **Focus Order**: Tabbing order must flow logically (left-to-right, top-to-bottom) following the visual layout.
- **No Keyboard Traps**: Users must be able to navigate into and out of all interactive widgets (e.g., modals, dropdowns) using only keyboard keys (`Tab`, `Shift+Tab`, `Esc`, `Enter`, `Space`).

### 2. Screen Reader Compatibility
- **Semantic HTML**: Use correct native tags (`<main>`, `<nav>`, `<header>`, `<footer>`, `<button>`, `<a>`) instead of generic nested `<div>` wrappers with custom click handlers.
- **ARIA Attributes**: Use standard ARIA roles (`role="dialog"`) and labels (`aria-label`, `aria-describedby`) only when native HTML tags cannot satisfy the requirement.
- **Image Alt Text**: Every image must have a descriptive `alt` attribute, or `alt=""` if the image is purely decorative.

### 3. Visual & Contrast
- **Color Contrast**: Text must satisfy a minimum contrast ratio of `4.5:1` for body text and `3:1` for large text against its background.
- **Non-Color Indicators**: Crucial information (error states, links, active tabs) must not be communicated using color alone (e.g., add underlines to inline links).

---

## 🧪 Testing Workflow

1. **Automated Audit**: Run automated auditing tools (such as Lighthouse, Axe Core, or Playwright A11y tests) to establish a baseline of clean violations.
2. **Keyboard-Only Run**: Navigate the page using only `Tab`, `Shift+Tab`, `Space`, `Enter`, and `Escape` to identify traps and focus indicators.
3. **Screen Reader Verification**: Verify interactive components (especially custom dropdowns and modals) using a screen reader (VoiceOver on macOS) to ensure states and roles are spoken correctly.

---

## 🔗 Related Skills

| Skill | Use For | Path |
|-------|---------|------|
| `a11y-debugging` | Practical debugging using Chrome DevTools | [a11y-debugging](file:///Users/gonzoblasco/.gemini/config/plugins/chrome-devtools-plugin/skills/a11y-debugging/SKILL.md) |
| `frontend-dev-guidelines` | Frontend standards and typography setups | [frontend-dev-guidelines](file:///Users/gonzoblasco/.gemini/config/skills/frontend-ui/frontend-dev-guidelines/SKILL.md) |
| `ui-review-nextjs-tailwind` | Reviewing layouts and visual styling | [ui-review-nextjs-tailwind](file:///Users/gonzoblasco/.gemini/config/skills/frontend-ui/ui-review-nextjs-tailwind/SKILL.md) |

---

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
