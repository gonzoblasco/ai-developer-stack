---
name: linear-expert
description: "Manage Linear issues, projects, and teams using MCP tools, CLI, or GraphQL API, adapted to our workspace reality."
risk: safe
source: community
date_added: "2026-06-26"
---

# Linear Expert

Tools and workflows for managing issues, projects, and teams in Linear.

---

## ⚠️ Tool Availability

This skill supports multiple interaction methods with Linear. Choose the best option for your current setup:

1. **MCP Tools (`stripe` or custom `linear` server)** - Check if a linear MCP server is configured in your workspace environment.
2. **Linear CLI (`linear` command)** - If installed on your system, use it for direct command-line interactions.
3. **cURL / GraphQL API** - Direct queries to Linear's GraphQL endpoint (`https://api.linear.app/graphql`) using `LINEAR_API_KEY` for maximum control and when helper tools are unavailable.

---

## 🔐 Credentials & Security

**CRITICAL**: Never expose API keys in terminal output or agent contexts.

### Safe Practices
- Store your `LINEAR_API_KEY` in your shell profile (`~/.zshrc` or `~/.bashrc`) or a local, uncommitted `.env` file.
- When validating if the key is set, do not print its value. Use:
  ```bash
  echo $LINEAR_API_KEY | cut -c 1-8 # Only show prefix if absolutely necessary for debugging
  ```

---

## 🚀 Common CLI Operations (If `linear` CLI is available)

```bash
# View an issue
linear issues view ENG-123

# Create an issue
linear issues create --title "Issue title" --description "Description"

# Update issue status
linear issues update ENG-123 -s "Done"

# Add a comment
linear issues comment add ENG-123 -m "Comment text"
```

---

## 📡 Direct GraphQL API Operations (Fallback)

When no CLI or MCP tools are available, you can perform direct GraphQL queries and mutations using `curl`.

### Query User Profile
```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: $LINEAR_API_KEY" \
  --data '{"query": "{ viewer { id name email } }"}' \
  https://api.linear.app/graphql
```

### Create Issue Mutation
```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: $LINEAR_API_KEY" \
  --data '{"query": "mutation { issueCreate(input: { title: \"New Feature\", description: \"Description of feature\", teamId: \"YOUR_TEAM_ID\" }) { success issue { id title } } }"}' \
  https://api.linear.app/graphql
```

---

## 📋 Project Planning & Management Workflow

### Issues ➔ Projects ➔ Initiatives

Every issue should ideally be attached to a project, and every project linked to an initiative.

1. **Create the Project First**: Ensure a clear objective is set before breaking down issues.
2. **Use Domain-Based Labels**:
   - **Type labels**: `feature`, `bug`, `refactor`, `chore`, `spike`
   - **Domain labels**: `security`, `backend`, `frontend`
   - **Scope labels**: `blocked`, `breaking-change`, `tech-debt`

---

## ⚠️ Limitations
- Only use this skill for Linear issue, project, or team management.
- Do not store plain text API keys inside files that are committed to git.
