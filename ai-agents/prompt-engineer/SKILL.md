---
name: prompt-engineer
description: "Transforms user prompts into optimized prompts using frameworks (RTF, RISEN, Chain of Thought, RODES, Chain of Density, RACE, RISE, STAR, SOAP, CLEAR, GROW)"
category: automation
risk: safe
source: community
tags: "[prompt-engineering, optimization, frameworks, ai-enhancement]"
date_added: "2026-02-27"
---

# Prompt Engineer Skill

Transforms raw, unstructured user prompts into highly optimized prompts using established prompting frameworks. It analyzes user intent, identifies task complexity, and intelligently selects the most appropriate framework(s) to maximize output quality.

The skill operates in "magic mode" - it works silently behind the scenes, only interacting with users when clarification is critically needed. Users receive polished, ready-to-use prompts without technical explanations or framework jargon.

This is a **universal skill** that works in any terminal context.

## When to Use
Invoke this skill when:
- User provides a vague or generic prompt (e.g., "help me code Python")
- User has a complex idea but struggles to articulate it clearly
- User's prompt lacks structure, context, or specific requirements
- Task requires step-by-step reasoning (debugging, analysis, design)
- User needs a prompt for a specific AI task but doesn't know prompting frameworks
- User wants to improve an existing prompt's effectiveness
- User asks variations of "how do I ask AI to..." or "create a prompt for..."

## Workflow

### Step 1: Analyze Intent
1. Read the raw prompt provided by the user.
2. Detect task characteristics:
   - **Type:** coding, writing, analysis, design, learning, planning, decision-making, creative, etc.
   - **Complexity:** simple (one-step), moderate (multi-step), complex (requires reasoning/design)
   - **Clarity:** clear intention vs. ambiguous/vague
   - **Domain:** technical, business, creative, academic, personal, etc.
3. Identify implicit requirements (examples needed, format specified, constraints).

### Step 2: Ask Clarifying Questions (Conditional)
Only ask if task type is completely ambiguous, target audience is unknown, or scope/format conflicts and cannot be inferred.
- Maximum 3 questions per invocation.
- Combine related questions.
- If enough context exists, skip this step entirely.

### Step 3: Select Framework(s)

| Task Type | Recommended Framework(s) | Rationale |
|-----------|-------------------------|-----------|
| **Role-based tasks** | **RTF** (Role-Task-Format) | Clear role definition + task + output format |
| **Step-by-step reasoning** | **Chain of Thought** | Encourages explicit reasoning steps |
| **Structured projects** | **RISEN** (Role, Instructions, Steps, End goal, Narrowing) | Comprehensive structure for complex work |
| **Complex design/analysis** | **RODES** (Role, Objective, Details, Examples, Sense check) | Balances detail with validation |
| **Summarization** | **Chain of Density** | Iterative refinement to essential info |
| **Communication** | **RACE** (Role, Audience, Context, Expectation) | Audience-aware messaging |
| **Investigation/analysis** | **RISE** (Research, Investigate, Synthesize, Evaluate) | Systematic analytical approach |
| **Contextual situations** | **STAR** (Situation, Task, Action, Result) | Context-rich problem framing |
| **Documentation** | **SOAP** (Subjective, Objective, Assessment, Plan) | Structured information capture |
| **Goal-setting** | **CLEAR** (Collaborative, Limited, Emotional, Appreciable, Refinable) | Goal clarity and actionability |
| **Coaching/development** | **GROW** (Goal, Reality, Options, Will) | Developmental conversation structure |

### Step 4: Generate and Format
- **Language Adaptation:** Generate prompts in the language the user wrote in (English, Portuguese, etc.).
- **Self-contained:** Make prompts complete, specific, and format-clear.
- **Output:** Present the optimized prompt in a clean Markdown code block.

## Critical Rules
- ❌ **NEVER** explain which framework was selected or why (magic mode - keep it invisible).
- ❌ **NEVER** include meta-commentary in the output ("This prompt uses...", "Note that...").
- ❌ **NEVER** ask more than 3 clarifying questions.
- ❌ **NEVER** present output without code block formatting.
- ✅ **ALWAYS** adapt prompt length to original input complexity.
- ✅ **ALWAYS** include output format specification in generated prompts.

## Related Skills
- [prompt-mastery](../prompt-mastery/SKILL.md) - Advanced prompting techniques, anti-injection patterns, and role structuring.
