---
name: ui-a11y
description: "Audit a StyleSeed-based component or page for WCAG 2.2 AA issues and apply practical accessibility fixes where the code makes them safe."
category: design
risk: safe
source: community
source_repo: bitjaru/styleseed
source_type: community
date_added: "2026-04-08"
author: bitjaru
tags: [ui, accessibility, wcag, audit, styleseed]
tools: [claude, cursor, codex, gemini]
---

# UI Accessibility Audit

Part of [StyleSeed](https://github.com/bitjaru/styleseed), this skill audits components and pages for accessibility issues with an emphasis on the Toss seed's mobile UI patterns. It combines WCAG 2.2 AA checks with practical code fixes for touch targets, focus states, contrast, labels, and reduced motion.

## When to Use
- Use when reviewing a page or component for accessibility regressions.
- Use when a StyleSeed UI looks polished but has uncertain keyboard or contrast behavior.
- Use when adding new interactive controls to a mobile-first screen.
- Use when you want a prioritized list of issues and fixable items.

## Audit Areas

### Perceivable
- **Text Contrast:** Ensure text contrast satisfies WCAG AA ratios.
- **Non-text Contrast:** Check contrast for controls and graphics.
- **Alt Text:** Verify alt text for images.
- **Icon Labels:** Add labels/attributes for meaningful icons.
- **No Color-Only Info:** Ensure no critical information is conveyed by color alone.

### Operable
- **Touch Targets:** Targets must be at least 44x44px.
- **Keyboard Reachability:** Ensure keyboard reachability for all interactive controls.
- **Logical Tab Order:** Verify logical tab order.
- **Visible Focus:** Implement visible focus indicators.
- **Reduced Motion:** Provide reduced-motion support for nonessential animation.

### Understandable
- **Input Labels:** Add visible labels or `aria-label` on inputs.
- **Field Association:** Ensure error text is associated with the correct field.
- **Wording:** Provide clear wording for errors and validation.
- **Language Setup:** Set document language appropriately.

### Robust
- **Semantic HTML:** Use semantic HTML where possible.
- **ARIA usage:** Correct use of ARIA when semantics alone are insufficient.
- **Control Semantics:** No faux buttons or links without the right roles and behavior.

## Output

When auditing, return:
1. **Issues Found:** Grouped by severity (Critical, Major, Minor).
2. **Safe Autofixes:** Code fixes that can be applied directly.
3. **Manual Review:** Items that need manual verification or product judgment.
4. **Summary:** A short summary of the accessibility risk level.

## Best Practices
- Fix semantics before layering on ARIA.
- Use design system tokens only if they still meet contrast requirements.
- Treat touch target failures as real usability defects, not polish issues.
- Prefer partial, verified fixes over speculative accessibility changes.

## Related Skills
- [accessibility-audit](../accessibility-audit/SKILL.md) - Broad compliance checklist and testing guidelines.
- [frontend-dev-guidelines](../frontend-dev-guidelines/SKILL.md) - General frontend standards.
- [ui-review-nextjs-tailwind](../ui-review-nextjs-tailwind/SKILL.md) - Reviewing layouts and styling.
