# 🤖 AI Engineering Playbook

> **"Autonomy is earned, not granted."**

This is the central engineering guide for building AI Agents and LLM-powered applications using the Antigravity Stack. It connects individual skills into a cohesive production workflow.

---

## 🏎️ The Agent Lifecycle

Building a production-grade agent is not just about writing a prompt. It requires a disciplined, multi-layered approach.

```mermaid
graph TD
    A[Phase 1: Brain & Personality] --> B[Phase 2: Hands & Capabilities]
    B --> C[Phase 3: Context & Memory]
    C --> D[Phase 4: Production & Safety]
```

### 🔵 Phase 1: Brain & Personality (Design)

_Goal: Define behavior, boundaries, and reasoning style._

1.  **Architect the Prompt**: Don't guess. Use **[`prompt-mastery`](prompt-mastery/SKILL.md)** to structure your System Instructions or dynamically optimize user queries using framework routing in **[`prompt-engineer`](prompt-engineer/SKILL.md)**.
    - _Critical_: Apply "Anti-Injection" patterns from day one.

2.  **Optimize Reasoning**: If the agent needs to solve complex problems, apply **[`prompt-mastery`](prompt-mastery/SKILL.md)** or framework mappings from **[`prompt-engineer`](prompt-engineer/SKILL.md)**.
    - Use **Few-Shot Prompting** to teach by example.
    - Use **Chain-of-Thought** to force step-by-step logic before answering.

### 🟠 Phase 2: Hands & Tools (Capabilities)

_Goal: Enable the agent to interact with the world reliably._

1.  **Design the Interface**: The LLM doesn't see your code; it sees your schemas. Use **[`agent-tool-builder`](agent-tool-builder/SKILL.md)**.
    - _Rule_: Clear descriptions > Complex logic.
    - _Validation_: Every tool must have a strict JSON Schema.

2.  **Connect External Services**: Use **[`mcp-builder`](mcp-builder/SKILL.md)** to wrap APIs (like GitHub, Slack, or Databases) into standard Model Context Protocol servers.

### 🟢 Phase 3: Memory & Knowledge (Context)

_Goal: Ground the agent in reality and your specific data._

1.  **Retrieve Knowledge**: Don't rely on the model's training data. Build a RAG pipeline using **[`rag-expert`](rag-expert/SKILL.md)**.
    - _Critical_: Implement **Semantic Chunking** and **Hybrid Search** (Keywords + Embeddings).
    - _Mandatory_: Always use a Reranker step.

2.  **Architecture Choice**: Choose the right structure using **[`ai-agents-architect`](ai-agents-architect/SKILL.md)**.
    - _ReAct_: For tasks requiring reasoning loops.
    - _Plan-Execute_: For complex, multi-step goals.

### 🔴 Phase 4: Production & Safety (Guardrails)

_Goal: Deploy without sleepless nights._

1.  **Enforce Limits**: Use **[`ai-agents-architect`](ai-agents-architect/SKILL.md)** patterns.
    - Implement **Permission Levels** (Auto vs. Ask User).
    - Set strict `max_iterations` loops to prevent infinite spending.

2.  **New Skill Creation**: If you discover a new reusable pattern during dev, create a new skill using the methodology in **[`meta-skill-antigravity`](meta-skill-antigravity/SKILL.md)**.

---

## 📚 Skill Index

| Skill | Focus Area | When to use |
| :--- | :--- | :--- |
| **[`prompt-mastery`](prompt-mastery/)** | Prompt Engineering | Optimizing prompts, Chain-of-Thought, templates |
| **[`prompt-engineer`](prompt-engineer/)** | Prompt Frameworks | Transforming generic requests using RTF, RISEN, RODES, etc. |
| **[`agent-tool-builder`](agent-tool-builder/)** | Tools & Functions | Designing JSON schemas for function calling |
| **[`ai-agents-architect`](ai-agents-architect/)** | Agent Reliability | Building loops, memory systems, safety checks, and multi-agent orchestration |
| **[`rag-expert`](rag-expert/)** | Knowledge/RAG | Building retrieval pipelines, chunking, reranking |
| **[`mcp-builder`](mcp-builder/)** | Connectivity | Creating MCP servers for external tools |
| **[`meta-skill-antigravity`](meta-skill-antigravity/)** | Methodology | Creating and validating new skills |
| **[`elon-musk`](elon-musk/)** | Simulation | Persona simulation for strategic decision-making |
