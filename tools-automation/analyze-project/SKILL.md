---
name: analyze-project
description: Forensic root cause analyzer for Antigravity sessions. Classifies scope deltas, rework patterns, root causes, hotspots, and auto-improves prompts/health.
risk: unknown
source: community
version: "1.0"
tags: [analysis, diagnostics, meta, root-cause, project-health, session-review]
---

# /analyze-project — Root Cause Analyst Workflow

Analyze AI-assisted coding sessions in `~/.gemini/antigravity/brain/` and produce a report that explains not just **what happened**, but **why it happened**, **who/what caused it**, and **what should change next time**.

## Goal

For each session, determine:
1. What changed from the initial ask to the final executed work.
2. Whether the main cause was user/spec, agent, repo/codebase, validation/testing, or task complexity.
3. Whether the opening prompt was sufficient.
4. Which files/subsystems repeatedly correlate with struggle.
5. What changes would most improve future sessions.

## When to Use
- You need a postmortem on AI-assisted coding sessions, especially when scope drift or repeated rework occurred.
- You want root-cause analysis that separates user/spec issues from agent mistakes, repo friction, or validation gaps.
- You need evidence-backed recommendations for improving future prompts, repo health, or delivery workflows.

## Global Rules
- Treat `.resolved.N` counts as **iteration signals**, not proof of failure.
- Separate **human-added scope**, **necessary discovered scope**, and **agent-introduced scope**.
- Separate **agent error** from **repo friction**.
- Every diagnosis must include **evidence** and **confidence** (High, Medium, Low).
- Evidence precedence: artifact contents > timestamps > metadata summaries > inference.

---

## Step-by-Step Analysis Workflow

### Step 0.5: Session Intent Classification
Classify the primary session intent from objective + artifacts:
- `DELIVERY`
- `DEBUGGING`
- `REFACTOR`
- `RESEARCH`
- `EXPLORATION`
- `AUDIT_ANALYSIS`

### Step 1: Discover Conversations
1. Read available conversation summaries from system context.
2. List conversation folders in the user’s Antigravity `brain/` directory.
3. Build a conversation index with: `conversation_id`, `title`, `objective`, `created`, `last_modified`.

### Step 2: Extract Session Evidence
For each conversation, read if present:
- Core artifacts (`task.md`, `implementation_plan.md`, `walkthrough.md`)
- Snapshots/versions (`task.md.resolved.*`, etc.)
- Metadata and timing parameters.

### Step 3: Prompt Sufficiency
Score the opening request on a 0–2 scale for:
- Clarity, Boundedness, Testability, Architectural specificity, Constraint awareness, and Dependency awareness.

### Step 4: Scope Change Classification
Classify scope change into:
- **Human-added scope** — new asks beyond the original task.
- **Necessary discovered scope** — work required to complete the original task correctly.
- **Agent-introduced scope** — likely unnecessary work introduced by the agent.

### Step 5: Rework Shape
Classify each session into one primary pattern:
- Clean execution, Early replan then stable finish, Progressive scope expansion, Reopen/reclose churn, Late-stage verification churn, Abandoned mid-flight, or Exploratory / research session.

### Step 6: Root Cause Analysis
For every non-clean session, assign a primary root cause:
- `SPEC_AMBIGUITY`, `HUMAN_SCOPE_CHANGE`, `REPO_FRAGILITY`, `AGENT_ARCHITECTURAL_ERROR`, `VERIFICATION_CHURN`, or `LEGITIMATE_TASK_COMPLEXITY`.

### Step 6.5: Session Severity Scoring (0–100)
Assign each session a severity score to prioritize attention:
- Completion failure (0–25), Replanning intensity (0–15), Scope instability (0–15), Rework shape severity (0–15), Prompt sufficiency deficit (0–10), Root cause impact (0–10), and Hotspot recurrence (0–10).
- Bands: **0–19 Low**, **20–39 Moderate**, **40–59 Significant**, **60–79 High**, **80–100 Critical**.

### Step 7: Subsystem / File Clustering
Identify whether friction is mostly prompt-driven, agent-driven, or concentrated in specific repo files/folders.

### Step 8: Comparative Cohorts
Compare first-shot successes vs re-planned sessions, completed vs abandoned, and high vs low prompt sufficiency to extract patterns.

### Step 9: Non-Obvious Findings
Generate 3–7 findings that are not simple metric restatements, backed by evidence.

### Step 10: Report Generation
Create `session_analysis_report.md` in the project directory following the prescribed markdown structure.

---

## Output Format (session_analysis_report.md)

```markdown
# 📊 Session Analysis Report — [Project Name]

**Generated**: [timestamp]  
**Conversations Analyzed**: [N]  
**Date Range**: [earliest] → [latest]

## Executive Summary
(Table of ratings for First-Shot Success, Completion Rate, Scope Growth, Replan Rate, Avg Severity.)

## Root Cause Breakdown
(Counts and percentages of root causes.)

## Prompt Sufficiency Analysis
(Analysis of sufficiency bands and ingredients.)

## Friction Hotspots
(List of files/subsystems associated with struggle.)

## Recommendations
(Observed pattern, Likely cause, Evidence, Change to make, Expected benefit.)
```

## Related Skills
- [docs-architect](../docs-architect/SKILL.md) - Documenting and mapping repository structures.
- [documentation-expert](../documentation-expert/SKILL.md) - Overall repository hygiene.
