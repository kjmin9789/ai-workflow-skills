---
name: requirements-architect
description: Use this skill to transform a planning document (e.g. from planning-refiner) into an implementation-ready requirements document — including IA, page-level requirements, user scenarios/UI states, and input validation rules.
---

# Requirements Architect

## Purpose

Convert a planning document into a structured requirements document:
information architecture, page-level requirements, scenario/state coverage,
and validation/error handling.

## Handoff from planning-refiner

This skill continues from `planning-refiner`, which writes:

```text
planning-docs/{YYYY-MM-DD}_{slug}/planning.md
```

(date/slug are just an example pattern, e.g.
`2026-06-15_conditional-order-form`)

- Always read this `planning.md` first and treat it as the source of truth
  — don't start from a blank slate or a one-line request.
- If no `planning.md` is found, ask the user for it before proceeding.
- Write the output as `requirements.md` in the same folder, so it stays
  paired with `planning.md` for `task-breakdown-planner`.

## Process

1. **Read `planning.md`.** Re-read goal, selected flow, and scope/out-of-scope
   — every requirement should trace back to these.

2. **Propose the page count**, with reasoning, a rough outline per page, and
   the tradeoff of reducing/expanding it. Then you MUST call the
   `AskUserQuestion` tool (do not just print the options as text) with
   these choices:
   1. 추천 페이지 수로 진행 (Recommended)
   2. 내가 페이지 수를 직접 지정
   3. 페이지 수 제한 없이 IA 기준으로 확장

   - If 2: ask for the desired count, then propose an IA fitting it.
   - If 3: drop the constraint and prioritize the clearest IA over minimum
     page count.

3. **Confirm IA page by page.** For each page, present name, purpose, IA
   sections, primary action, CTA, and key metric (if relevant), then you
   MUST call the `AskUserQuestion` tool (do not just print the options as
   text) with these choices:
   1. 승인 (Recommended)
   2. 수정하고 진행
   3. 이 페이지 제거

   Don't move to the next page, or generate the final document, until each
   page is confirmed.

4. **Define functional requirements** (FR1, FR2, ...) — specific and
   testable (not "support notifications" but "user can toggle each category
   independently").

5. **Define page-level requirements** — purpose, IA placement, primary
   action, CTA, and metric. Exactly one primary action per page.

6. **Derive scenarios and UI states**, generalized from the planning
   document (not a single hardcoded example): input/state-driven UI changes,
   permission/status variants, normal/empty/loading/error/success states,
   CTA enable/disable conditions.

7. **Define input validation and error states** — rule, error message,
   system behavior for each input/state that can fail or vary.

8. **List open questions** — anything unresolved goes under 확인 필요 사항;
   don't invent business rules.

9. **Generate `requirements.md`** — only after steps 2–3 are confirmed
   (unless the user explicitly said to proceed automatically).

## Output format

See [requirements-template.md](requirements-template.md) for the full
template:

1. 요약
2. 페이지 수
3. IA
4. 기능 요구사항
5. 페이지별 요구사항
6. 주요 시나리오 / 상태 케이스
7. 입력값 검증 / 에러 상태
8. 확인 필요 사항

## Rules

- Ask only one confirmation question at a time.
- Don't create implementation tasks, task owners, or engineering tickets —
  that's `task-breakdown-planner`'s job.

This output is ready to be passed to `task-breakdown-planner`.
