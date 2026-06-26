---
name: wcag-audit-patterns
description: "Comprehensive guide to auditing web content against WCAG 2.2 guidelines with actionable remediation strategies."
risk: safe
source: community
date_added: "2026-02-27"
---

# WCAG Audit Patterns

Comprehensive guide to auditing web content against WCAG 2.2 guidelines with actionable remediation strategies.

## Use this skill when

- Conducting accessibility audits
- Fixing WCAG violations
- Implementing accessible components
- Preparing for accessibility lawsuits
- Meeting ADA/Section 508 requirements
- Achieving VPAT compliance

## Do not use this skill when

- You need legal advice or formal certification
- You only want a quick automated scan without manual verification
- You cannot access the UI or source for remediation work

## Instructions

1. **Automated Scanning**: Run automated tools (axe, Lighthouse, WAVE) to collect initial quick findings.
2. **Manual Verification**: Perform manual checks for keyboard navigation (focus indicators, focus trap, tab order) and screen reader behavior (VoiceOver).
3. **Map and Document**: Map each issue to a WCAG 2.2 criterion, assign severity (Critical, Major, Minor), and propose code remediation.
4. **Re-Test**: Re-test after fixes and document residual risk and compliance status.

---

## 🛠️ WCAG 2.2 Core Checklist & Remediation

### 1. Perceivable (Text & Layout)
- **Contrast (1.4.3 / 1.4.11):** Text must be >= 4.5:1 (3:1 for large text). Interactive components and graphical elements must be >= 3:1.
- **Alt Text (1.1.1):** Provide `alt` description for images. Use empty `alt=""` for decorative assets.
- **Use of Color (1.4.1):** Never convey status or info using color alone. Provide text labels or distinct visual patterns.

### 2. Operable (Interactions)
- **Keyboard (2.1.1):** All functionality must be operable via keyboard (`Tab`, `Shift+Tab`, `Space`, `Enter`, `Escape`).
- **Focus Visible (2.4.7) & Focus Order (2.4.3):** Ensure a clear focus ring is visible and moves in a logical reading order.
- **Touch Target Size (2.5.8 - WCAG 2.2):** Ensure pointer targets are at least 24x24px, or have sufficient spacing (preferring 44x44px for primary controls as detailed in [ui-a11y](../ui-a11y/SKILL.md)).

### 3. Understandable (Input & Form Help)
- **Error Identification (3.3.1) & Labels (3.3.2):** Inputs must have visible labels or programmatically linked attributes (`aria-label`, `aria-labelledby`). Error messages must clearly describe the problem and point to the invalid input.

### 4. Robust (Code Standards)
- **Status Messages (4.1.3):** Dynamic content updates must be announced to assistive technologies using ARIA live regions (`aria-live="polite"`).

## Related Skills
- [accessibility-audit](../accessibility-audit/SKILL.md) - Baseline WCAG audit and testing workflow.
- [ui-a11y](../ui-a11y/SKILL.md) - Mobile-first component auditing and autofix patterns.
