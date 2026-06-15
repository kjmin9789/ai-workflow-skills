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

## Interaction protocol

Do not write the final `requirements.md` immediately. First confirm the
page structure with the user, one decision at a time, using
`AskUserQuestion` so the user can pick with a click instead of typing.

Skip a confirmation step only if the user has explicitly said to proceed
automatically.

### Step 1. Page count

After reading the planning document, propose a recommended page count with:

- Recommended page count and reasoning
- A rough outline of what each page would contain
- The tradeoff of reducing the page count
- The tradeoff of expanding the page count

Then ask the user to choose, via `AskUserQuestion`, one of:

1. 추천 페이지 수로 진행 (Recommended)
2. 내가 페이지 수를 직접 지정
3. 페이지 수 제한 없이 IA 기준으로 확장

Behavior by choice:

- **1 (recommended count)** — proceed with the recommended count and move to
  Step 2.
- **2 (custom count)** — ask the user for the number of pages, then propose
  an IA that fits that count, then move to Step 2.
- **3 (no constraint)** — drop the page-count constraint and propose an IA
  based on clarity, usability, and feature complexity; briefly explain why
  the expanded IA is better than the minimum.

### Step 2. IA per page

Confirm the IA one page at a time. For each page, present:

- Page name and purpose
- IA / main sections
- Primary action
- CTA
- Key metric (if relevant)

Then ask the user to choose, via `AskUserQuestion`, one of:

1. 승인 (Recommended)
2. 수정하고 진행
3. 이 페이지 제거

Do not move to the next page until the current page's IA is confirmed. Do
not generate the final `requirements.md` until all pages are confirmed.

### Step 3. Final requirements document

Only after the page count and every page's IA are confirmed, generate the
full requirements document.

## Process

1. **Understand the goal and scope.**
   - Re-read the goal, selected flow, and scope/out-of-scope before writing
     anything — every requirement should trace back to these.

2. **Propose and confirm the page count.** (Interaction protocol, Step 1)

3. **Propose and confirm the IA for each page.** (Interaction protocol,
   Step 2)
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

9. **Generate the final requirements document.** (Interaction protocol,
   Step 3)

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
- Before writing the final requirements document, ask the user to confirm
  the page count using `AskUserQuestion` (or a numbered list if selectable
  choices aren't supported).
- The user can approve the recommended page count, specify a different page
  count, or remove the page count constraint.
- After page count confirmation, confirm the IA for each page one by one
  using `AskUserQuestion`.
- Ask only one confirmation question at a time.
- Do not create the final `requirements.md` until the page count and every
  page's IA are confirmed, unless the user explicitly asks to proceed
  automatically.
- If the user removes the page count constraint, prioritize the clearest IA
  over the minimum number of pages.
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

This output is ready to be passed to `task-breakdown-planner`.
