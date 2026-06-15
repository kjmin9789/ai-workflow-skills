---
name: requirements-architect
description: Use this skill to transform a planning document (e.g. from planning-refiner) into an implementation-ready requirements document — including IA, page-level requirements, user scenarios/UI states, and input validation rules.
---

# Requirements Architect

## Purpose

Convert a planning document into a requirements document: IA, page-level
requirements, scenario/state coverage, and validation/error handling.

## Handoff

Continues from `planning-refiner`, which writes
`planning-docs/{YYYY-MM-DD}_{slug}/planning.md` (date/slug are just an
example, e.g. `2026-06-15_conditional-order-form`).

- Read that `planning.md` first as the source of truth; if missing, ask the
  user for it.
- Write output to `requirements.md` in the same folder.

## Process

1. **Read `planning.md`** — goal, selected flow, scope/out-of-scope. Every
   requirement must trace back to these.

2. **Propose page count** (reasoning, rough outline per page,
   tradeoff of fewer/more pages). Then you MUST call `AskUserQuestion`
   (not plain text):
   1. 추천 페이지 수로 진행 (Recommended)
   2. 내가 페이지 수를 직접 지정
   3. 페이지 수 제한 없이 IA 기준으로 확장

   2 → ask for the count, propose IA for it. 3 → drop the constraint,
   prioritize clearest IA.

3. **Confirm IA page by page** — name, purpose, IA sections, primary
   action, CTA, key metric. Then you MUST call `AskUserQuestion` (not plain
   text):
   1. 승인 (Recommended)
   2. 수정하고 진행
   3. 이 페이지 제거

   Don't proceed past an unconfirmed page.

4. **Write the requirements document**, covering:
   - 기능 요구사항 (FR1, FR2, ... — specific and testable)
   - 페이지별 요구사항 (purpose, IA, one primary action, CTA, metric)
   - 주요 시나리오 / 상태 케이스 (generalized from the plan — input/state/
     permission variants, empty/loading/error/success, CTA enable/disable)
   - 입력값 검증 / 에러 상태 (rule, error message, system behavior)
   - 확인 필요 사항 (open questions — don't invent business rules)

## Output format

See [requirements-template.md](requirements-template.md):
요약 → 페이지 수 → IA → 기능 요구사항 → 페이지별 요구사항 → 주요 시나리오 /
상태 케이스 → 입력값 검증 / 에러 상태 → 확인 필요 사항

## Rules

- Ask one confirmation question at a time; skip 2–3 only if the user said
  to proceed automatically.
- No implementation tasks/owners/tickets — that's `task-breakdown-planner`'s
  job.
