# ai-workflow-skills

Reusable AI skills for product planning, requirements writing, and task breakdown.

This repository contains a set of AI workflow skills that support the product
development process end-to-end — from a rough idea to a trackable task list.
The three skills are designed to be used **in sequence**, each one's output
feeding the next skill's input.

## Skills

| Skill | What it does | Path |
|---|---|---|
| `planning-refiner` | Refines a rough product idea or planning note into a structured product plan (problem, users, goal, scope, risks, open questions) | [skills/planning-refiner/SKILL.md](skills/planning-refiner/SKILL.md) |
| `requirements-architect` | Converts a product plan into implementation-ready requirements (functional/non-functional requirements, user stories, acceptance criteria) | [skills/requirements-architect/SKILL.md](skills/requirements-architect/SKILL.md) |
| `task-breakdown-planner` | Breaks requirements into a trackable task list across design, engineering, QA, and release | [skills/task-breakdown-planner/SKILL.md](skills/task-breakdown-planner/SKILL.md) |

## Worked example

Each skill's `examples/` folder contains a real `input.md` and `output.md`
for the same running example — **"in-app notification settings
improvement"** — so you can see how a one-line idea turns into a plan, then
into requirements, then into a task list, with each skill's output becoming
the next skill's input:

```text
planning-refiner/examples/output.md
  -> requirements-architect/examples/input.md
       -> requirements-architect/examples/output.md
            -> task-breakdown-planner/examples/input.md
                 -> task-breakdown-planner/examples/output.md
```

## Templates

The `templates/` folder contains the blank output structure used by each
skill, so they can also be filled in manually without an AI:

- [templates/planning-template.md](templates/planning-template.md)
- [templates/requirements-template.md](templates/requirements-template.md)
- [templates/task-template.md](templates/task-template.md)

## Download

Download all skills as a ZIP:

https://github.com/kjmin9789/ai-workflow-skills/archive/refs/heads/main.zip

## Repository structure

```text
ai-workflow-skills/
├── README.md
├── skills/
│   ├── planning-refiner/
│   │   ├── SKILL.md
│   │   └── examples/
│   │       ├── input.md
│   │       └── output.md
│   ├── requirements-architect/
│   │   ├── SKILL.md
│   │   └── examples/
│   │       ├── input.md
│   │       └── output.md
│   └── task-breakdown-planner/
│       ├── SKILL.md
│       └── examples/
│           ├── input.md
│           └── output.md
├── templates/
│   ├── planning-template.md
│   ├── requirements-template.md
│   └── task-template.md
└── LICENSE
```

## Purpose

These skills demonstrate how AI can support a practical product workflow:

- Clarifying and refining a rough product idea
- Defining structured, implementation-ready requirements
- Breaking requirements into actionable, owned tasks
