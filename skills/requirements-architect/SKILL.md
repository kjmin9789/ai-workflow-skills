---
name: requirements-architect
description: Use this skill to transform a planning document (e.g. from planning-refiner) into an implementation-ready requirements document — including IA, page-level requirements, user scenarios/UI states, and input validation rules.
---

# Requirements Architect

## Purpose

This skill converts a planning document into a structured requirements
document that design and engineering can build against: information
architecture, page-level requirements, scenario/state coverage, and
validation/error handling.

## When to use

Use this skill when the user provides:

- A planning document (e.g., the output of `planning-refiner`)
- A feature concept with a defined scope
- A product plan that needs to be turned into buildable requirements

## Process

1. **Understand the goal and scope.**
   - Re-read the goal, selected flow, and scope/out-of-scope before writing
     anything — every requirement should trace back to these.

2. **Decide the page count.**
   - What is the minimum number of pages/screens needed to deliver the
     scope?
   - State the reasoning — why this count is sufficient and not more or
     fewer.

3. **Structure the IA (Information Architecture).**
   - Define IA before writing page-level requirements.
   - Show depth/hierarchy, the components on each level, and their purpose.

4. **Define functional requirements.**
   - Is each requirement specific and testable (not "support notifications"
     but "user can toggle each category independently")?
   - Number them (FR1, FR2, ...) for traceability.

5. **Define page-level requirements.**
   - For each page: purpose, where it sits in the IA, primary action, CTA,
     and the metric it should move (if any).
   - Each page must have exactly one clear primary action.

6. **Derive scenarios and UI states.**
   - For each page/feature, work through:
     - Does the UI change based on user input or state?
     - Does the UI change based on user permission/status?
     - Are there normal / abnormal / empty / completed states?
     - Are there CTA enable/disable conditions?
     - Are there error, warning, or success states?
   - Generalize these from the planning document — don't hardcode a single
     example.

7. **Define input validation and error states.**
   - For each input/state that can fail or vary: the rule, the error
     message, and the resulting system behavior.

8. **List open questions.**
   - What needs to be confirmed before implementation, and what business
     rules were not specified in the plan?

## Output format

Return the requirements document using the following structure. See
[requirements-template.md](requirements-template.md) for the full template.

1. 요약
2. 페이지 수
3. IA
4. 기능 요구사항
5. 페이지별 요구사항
6. 주요 시나리오 / 상태 케이스
7. 입력값 검증 / 에러 상태
8. 확인 필요 사항

## Rules

- Do not write requirements for only one fixed example.
- Treat the input planning document as the source of truth.
- Always decide and state the minimum required page count.
- Always explain why the selected page count is sufficient.
- Always define IA before page-level requirements.
- Each page must have one clear primary action.
- Include multiple user scenarios or UI states when the feature behavior
  changes based on user input, user status, system status, or validation
  state.
- Scenario cases should be generalized from the planning document, not
  hardcoded from a single example.
- Do not create implementation tasks, task owners, or engineering tickets.
- Do not invent unresolved business rules. Put them under 확인 필요 사항.

## Example

- [examples/input.md](examples/input.md) — a plan from `planning-refiner`
- [examples/output.md](examples/output.md) — the resulting requirements

This output is ready to be passed to `task-breakdown-planner`, whose example
input is these requirements.
