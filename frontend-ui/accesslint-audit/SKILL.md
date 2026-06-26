---
name: accesslint-audit
description: "Find and fix WCAG 2.2 accessibility issues. Two modes — report (sweep a codebase or page, produce a prioritized written report, no edits) and fix (audit→edit→verify loop on a target). Prefers direct-CDP live-DOM auditing; falls back to a browser-MCP composition or HTML-string audits."
risk: safe
source: "https://github.com/AccessLint/skills"
date_added: "2026-06-02"
---

# AccessLint Audit & Fix

Find and fix WCAG 2.2 accessibility issues using live DOM / Chrome DevTools Protocol (CDP) or HTML/JSX static audits. Supports Report Mode (prioritized audits, no edits) and Fix Mode (audit-edit-verify loop).

## When to Use
- Use when requested to find and fix WCAG 2.2 accessibility issues.
- Use when reviewing a codebase or page for keyboard, contrast, semantic, and ARIA violations.
- Use when you need a structured audit-edit-verify cycle to fix accessibility regressions.

## Modes of Operation

### 1. Report Mode
- **Triggers:** "audit my codebase", "review components/", "what's wrong with this page?", "give me an a11y report".
- **Action:** Audit targets and generate a prioritized report. **Do not edit files.**

### 2. Fix Mode
- **Triggers:** "fix the a11y issues in X", "audit and fix", "make this accessible", "verify the contrast fix landed".
- **Action:** Execute the Audit → Edit → Verify cycle on target files.

---

## Audit Flows (In Order of Preference)

1. **`audit_live`**: Connects to a running Chrome debug session or auto-launches Chrome minimized. Try first for URLs.
2. **`audit-live-page`**: Use when connected via a browser MCP (chrome-devtools-mcp, playwright-mcp, puppeteer-mcp) on a specific page state.
3. **`audit_html`**: Used for raw HTML strings, static files, or compiled JSX. Falls back to static code checks.

---

## Report Format (Report Mode)

```markdown
# Accessibility audit — <scope>

## Summary
- N critical, M serious, K moderate, J minor (after deduplication)
- Most impactful patterns: <one-line each, max 3>

## Critical (blocks access)
- **Pattern**: <one-line description>
- **WCAG**: <ID> — <name>
- **Affected files**: <file:line> (×N if repeated)
- **Fix**: <directive or specific code change>
- **Why critical**: <user impact>

## Serious
[same shape]

## Moderate / Minor
[deduplicated by rule]

## Recommendations
- Architectural / pattern-level improvements and manual tests.
```

---

## Fix Mode Lifecycle

1. **Baseline:** Run audit with `name: "before"` and `format: "compact"`.
2. **Plan & Edit:**
   - Locate code pointers via React DevTools fiber `Source:` tags (`file:line`) or fallback to selectors.
   - Apply mechanical fixes verbatim. Leave `TODO` annotations with the rule ID for contextual/visual issues.
3. **Verify:** Run `audit_diff({ audit_name: "before" })` to confirm fixes.

## Related Skills
- [accessibility-audit](../accessibility-audit/SKILL.md) - Broad WCAG compliance and keyboard testing guidelines.
- [ui-a11y](../ui-a11y/SKILL.md) - Mobile-first component auditing and autofix patterns.
- [wcag-audit-patterns](../wcag-audit-patterns/SKILL.md) - Deep WCAG 2.2 checklists and checklists mapping.
