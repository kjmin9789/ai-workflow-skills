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

All three SKILL.md files share a single running example — **"in-app
notification settings improvement"** — so you can see how a one-line idea
turns into a plan, then into requirements, then into a task list, with each
skill's output becoming the next skill's input.

## Download

Download all skills as a ZIP:

https://github.com/kjmin9789/ai-workflow-skills/archive/refs/heads/main.zip

## Repository structure

```text
ai-workflow-skills/
├── README.md
├── skills/
│   ├── planning-refiner/
│   │   └── SKILL.md
│   ├── requirements-architect/
│   │   └── SKILL.md
│   └── task-breakdown-planner/
│       └── SKILL.md
└── LICENSE
```

## Purpose

These skills demonstrate how AI can support a practical product workflow:

- Clarifying and refining a rough product idea
- Defining structured, implementation-ready requirements
- Breaking requirements into actionable, owned tasks
