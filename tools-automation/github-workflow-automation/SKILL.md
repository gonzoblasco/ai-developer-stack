---
name: github-workflow-automation
description: "Patterns for automating GitHub workflows with AI assistance, inspired by [Gemini CLI](https://github.com/google-gemini/gemini-cli) and modern DevOps practices."
risk: critical
source: community
date_added: "2026-02-27"
---

# 🔧 GitHub Workflow Automation

Patterns for automating GitHub workflows with AI assistance, inspired by [Gemini CLI](https://github.com/google-gemini/gemini-cli) and modern DevOps practices.

## When to Use This Skill

Use this skill when:
- Automating PR reviews with AI
- Setting up issue triage automation
- Creating GitHub Actions workflows
- Integrating AI into CI/CD pipelines
- Automating Git operations (rebases, cherry-picks)

---

## 1. Automated PR Review

### 1.1 PR Review Action

```yaml
# .github/workflows/ai-review.yml
name: AI Code Review

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  review:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write

    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Get changed files
        id: changed
        run: |
          files=$(git diff --name-only origin/${{ github.base_ref }}...HEAD)
          echo "files<<EOF" >> $GITHUB_OUTPUT
          echo "$files" >> $GITHUB_OUTPUT
          echo "EOF" >> $GITHUB_OUTPUT

      - name: Get diff
        id: diff
        run: |
          diff=$(git diff origin/${{ github.base_ref }}...HEAD)
          echo "diff<<EOF" >> $GITHUB_OUTPUT
          echo "$diff" >> $GITHUB_OUTPUT
          echo "EOF" >> $GITHUB_OUTPUT

      - name: AI Review
        uses: actions/github-script@v7
        with:
          script: |
            const { Anthropic } = require('@anthropic-ai/sdk');
            const client = new Anthropic({ apiKey: process.env.ANTHROPIC_API_KEY });

            const response = await client.messages.create({
              model: "claude-3-sonnet-20240229",
              max_tokens: 4096,
              messages: [{
                role: "user",
                content: `Review this PR diff and provide feedback:
                
                Changed files: ${{ steps.changed.outputs.files }}
                
                Diff:
                ${{ steps.diff.outputs.diff }}
                
                Provide:
                1. Summary of changes
                2. Potential issues or bugs
                3. Suggestions for improvement
                4. Security concerns if any
                
                Format as GitHub markdown.`
              }]
            });

            await github.rest.pulls.createReview({
              owner: context.repo.owner,
              repo: context.repo.repo,
              pull_number: context.issue.number,
              body: response.content[0].text,
              event: 'COMMENT'
            });
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
```

### 1.2 Review Comment Patterns

```markdown
# AI Review Structure

## 📋 Summary
Brief description of what this PR does.

## ✅ What looks good
- Well-structured code
- Good test coverage
- Clear naming conventions

## ⚠️ Potential Issues
1. **Line 42**: Possible null pointer exception
   ```javascript
   user?.profile?.name ?? "Unknown";
   ```
2. **Line 78**: Consider error handling

## 💡 Suggestions
- Consider extracting validation logic.
- Add JSDoc comments.

## 🔒 Security Notes
- No sensitive data exposure detected.
```

---

## 2. Issue Triage Automation

### 2.1 Auto-label Issues

```yaml
# .github/workflows/issue-triage.yml
name: Issue Triage

on:
  issues:
    types: [opened]

jobs:
  triage:
    runs-on: ubuntu-latest
    permissions:
      issues: write

    steps:
      - name: Analyze issue
        uses: actions/github-script@v7
        with:
          script: |
            const issue = context.payload.issue;
            const analysis = await analyzeIssue(issue.title, issue.body);
            const labels = [];

            if (analysis.type === 'bug') {
              labels.push('bug');
              if (analysis.severity === 'high') labels.push('priority: high');
            } else if (analysis.type === 'feature') {
              labels.push('enhancement');
            } else if (analysis.type === 'question') {
              labels.push('question');
            }

            if (analysis.area) {
              labels.push(`area: ${analysis.area}`);
            }

            await github.rest.issues.addLabels({
              owner: context.repo.owner,
              repo: context.repo.repo,
              issue_number: issue.number,
              labels: labels
            });
```

---

## 3. CI/CD Integration

### 3.1 Smart Test Selection

```yaml
# .github/workflows/smart-tests.yml
name: Smart Test Selection

on:
  pull_request:

jobs:
  analyze:
    runs-on: ubuntu-latest
    outputs:
      test_suites: ${{ steps.analyze.outputs.suites }}

    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Analyze changes
        id: analyze
        run: |
          changed=$(git diff --name-only origin/${{ github.base_ref }}...HEAD)
          suites="[]"

          if echo "$changed" | grep -q "^src/api/"; then
            suites=$(echo $suites | jq '. + ["api"]')
          fi

          if echo "$changed" | grep -q "^src/frontend/"; then
            suites=$(echo $suites | jq '. + ["frontend"]')
          fi

          echo "suites=$suites" >> $GITHUB_OUTPUT
```

---

## Best Practices

### Security
- [ ] Store API keys in GitHub Secrets.
- [ ] Use minimal permissions in workflows.
- [ ] Validate all inputs.

### Performance
- [ ] Cache dependencies.
- [ ] Use matrix builds for parallel testing.
- [ ] Skip unnecessary jobs with path filters.

## Related Skills
- [n8n-workflow-builder](../n8n-workflow-builder/SKILL.md) - Workflow automation, webhooks, and Cron events.
- [vibers-code-review](../vibers-code-review/SKILL.md) - Human review triggers and PR checklist sync.
