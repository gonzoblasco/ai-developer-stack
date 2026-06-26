---
name: web-design-guidelines
description: "Review files for compliance with Web Interface Guidelines."
risk: safe
source: community
date_added: "2026-02-27"
---

# Web Interface Guidelines

Review files for compliance with Web Interface Guidelines.

## How It Works

1. Fetch the latest guidelines from the source URL below.
2. Read the specified files (or prompt user for files/pattern).
3. Check against all rules in the fetched guidelines.
4. Output findings in the terse `file:line` format.

## Guidelines Source

Fetch fresh guidelines before each review:
```
https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md
```
Use a tool like `read_url_content` to retrieve the latest rules. The fetched content contains all the rules and output format instructions.

## Usage

When a user provides a file or pattern argument:
1. Fetch guidelines from the source URL above.
2. Read the specified files.
3. Apply all rules from the fetched guidelines.
4. Output findings using the format specified in the guidelines.

If no files are specified, ask the user which files to review.

## Related Skills
- [ui-review-nextjs-tailwind](../ui-review-nextjs-tailwind/SKILL.md) - Code and design layout audits.
- [frontend-dev-guidelines](../frontend-dev-guidelines/SKILL.md) - Reusable components and standards checks.
