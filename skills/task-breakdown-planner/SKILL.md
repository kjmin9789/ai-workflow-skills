---
name: task-breakdown-planner
description: Use this skill to turn planning.md + requirements.md into an MVP-scoped task breakdown, drive AI-assisted implementation, verify scenarios, and write a handoff. Use when the user wants to start building from a planning/requirements pair.
---

# Task Breakdown Planner

## Purpose

Take `planning.md` and `requirements.md`, scope an MVP, break it into
implementation tasks, drive AI-assisted implementation, verify key
scenarios, and end with a handoff.

## Handoff (input)

Continues from `requirements-architect`, which writes
`planning-docs/{YYYY-MM-DD}_{slug}/{planning.md, requirements.md}`
(date/slug are just an example).

- Read both files first; if either is missing, ask the user for it.
- Write output to `task-workflow.md` in the same folder.

## Process

1. **Read `planning.md` and `requirements.md`** — goal, flow, scope/out of
   scope, IA, FRs, scenarios, validation/error states. Decide what must be
   built vs. not.

2. **Propose MVP scope** — core input/output, core logic, core UI states,
   CTA enable/disable, success state, minimal error handling (defer real
   API integration, full responsive design, animations, tests, multi-page
   expansion). Then you MUST call the `AskUserQuestion` tool (do not print
   the options as text):
   1. 제안된 MVP 범위로 진행 (Recommended)
   2. 범위 조정 (포함/제외 항목 변경)

   Excluded items must still be recorded in the final handoff.

3. **Break into tasks** — implementation-order units (e.g. 화면 구조 →
   입력 상태 → 핵심 로직 → 검증/에러 → CTA/성공 상태 → 시나리오 확인 →
   handoff). Each task: 목적 / 구현 내용 / 완료 기준. Then you MUST call the
   `AskUserQuestion` tool (do not print the options as text):
   1. 이 순서로 진행 (Recommended)
   2. Task 순서/구성 조정

4. **Write the AI implementation request** for each task: 목표 / 입력 /
   출력 / 핵심 로직 / UI 상태 (초기·정상·오류·비활성화·성공) / 제약 (기술
   스택, API 연동 여부, 스타일링 우선순위, 접근성).

5. **Review implementation output** — 요구사항 누락, 입력값 검증, CTA
   조건, 시나리오 동작, 범위를 넘는 임의 동작, 기록되지 않은 가정.

6. **Verify scenarios** from `requirements.md` — at minimum: 초기 진입,
   정상/오류 입력, CTA 비활성화/활성화, 성공 상태, 주요 토글/상태 변경.
   Manual confirmation is fine under time pressure.

7. **Write the handoff** — always required: 구현 완료 항목 / 주요 의사결정
   / 확인한 시나리오 / 가정한 내용 / 남은 리스크 / 다음 개선 제안.

## Confirmation rule

Any time this skill needs the user to decide between a small set of options
(MVP scope, task order, or anything similar), call the `AskUserQuestion`
tool to present clickable choices instead of asking in plain text. Ask one
question at a time.

## Output format

See [task-template.md](task-template.md):
요약 → MVP 범위 / 제외 범위 → Task List → AI 구현 요청 → 시나리오 검증 →
Handoff → Definition of Done

## Rules

- Don't implement before reading `planning.md` and `requirements.md`.
- Don't expand scope beyond requirements or build excluded items.
- Don't finish with only the happy path — cover error states.
- Never end without a handoff.
