# ✍️ Skill Authoring Playbook

This playbook outlines the standards, guidelines, and core philosophies for authoring predictable and effective AI agent skills.

## Skills Available

| Skill | Description | Target |
| --- | --- | --- |
| [writing-great-skills](writing-great-skills/SKILL.md) | Vocabulary, information hierarchy, and principles for writing predictable skills | Agent Engineering |

## Philosophy

1. **Predictability is Key**: A skill exists to make the agent's execution process predictable and consistent.
2. **Context Window Hygiene**: Balance model-invoked vs. user-invoked configurations to optimize the context load.
3. **Progressive Disclosure**: Keep `SKILL.md` clean and concise by pushing deep references and examples into separate files/folders.
4. **Leading Words**: Recruit the model's pretrained concepts (e.g., *red loop*, *Gemba*) to anchor complex behaviors in fewer tokens.
