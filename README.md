# AI Workflow Skills

Reusable AI skills for turning product ideas into plans, requirements, and actionable tasks.

> 기획 아이디어를 제품 기획서, 요구사항, 실행 태스크로 구조화하는 AI workflow skill 모음입니다.

## Skills

| Skill                    | Purpose                                                        | Path                                     |
| ------------------------ | -------------------------------------------------------------- | ---------------------------------------- |
| `planning-refiner`       | Refines rough product ideas into structured product plans.     | `skills/planning-refiner/SKILL.md`       |
| `requirements-architect` | Converts product plans into implementation-ready requirements. | `skills/requirements-architect/SKILL.md` |
| `task-breakdown-planner` | Breaks requirements into clear, trackable tasks.               | `skills/task-breakdown-planner/SKILL.md` |

## Workflow

These skills are designed to be used in sequence:

```text
Idea
→ Product Plan
→ Requirements
→ Task List
```

`requirements-architect` and `task-breakdown-planner` each include an
`examples/` folder with sample input and output files; `planning-refiner`
keeps its example inline in `SKILL.md`. The output of one skill's example
feeds into the next skill's example input.

```text
skills/
├── planning-refiner/
├── requirements-architect/
└── task-breakdown-planner/
```

## Templates

The `templates/` folder includes reusable blank templates for:

* Product planning
* Requirements definition
* Task breakdown

## Download

Download all skills as a ZIP:

```text
https://github.com/kjmin9789/ai-workflow-skills/archive/refs/heads/main.zip
```
