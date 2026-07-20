# AGENTS.md — AI Developer Stack

## Qué es

Repositorio de skills/playbooks para ingeniería con IA. 80+ skills en 9 playbooks. Stack: Markdown puro.

## Estructura

```
ai-developer-stack/
├── .knowledge/          # Memoria de sesión (workspace git)
│   ├── BRIEF.md
│   ├── EVALUATION.md
│   ├── DEFINITION.md
│   ├── ROADMAP.md
│   └── STATUS.md
├── ai-agents/           # Playbook + skills de IA
├── backend-infra/       # Playbook + skills de backend
├── frontend-ui/         # Playbook + skills de frontend
├── fullstack/           # Playbook + skills fullstack
├── growth/              # Playbook + skills de crecimiento
├── languages-standards/ # Playbook + skills de lenguajes/testing
├── product-building/    # Playbook + skills de producto
├── skill-authoring/     # Playbook + skills de creación de skills
├── strategy-architecture/ # Playbook + skills de estrategia/arquitectura
├── tools-automation/    # Playbook + skills de automatización
├── docs/                # Dashboard web
├── README.md            # Capability map + índice
└── CHANGELOG.md         # Historial de releases
```

## Convenciones

- Cada skill tiene su carpeta con SKILL.md
- Cada playbook tiene README.md en la raíz de su carpeta
- Links internos relativos (sin https://github.com/...)
- CHANGELOG.md en raíz con formato Keep a Changelog
- README.md con capability map completo

## Próximos Pasos (v2.0)

1. CI/CD Pipeline (GitHub Actions)
2. Tests de consistencia estructural
3. Metadatos YAML en skills
4. Generación automática de capability map
