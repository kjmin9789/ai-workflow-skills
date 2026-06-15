---
name: task-breakdown-planner
description: Use this skill to turn planning.md + requirements.md into an MVP-scoped task breakdown, drive AI-assisted implementation, verify scenarios, and write a handoff. Use when the user wants to start building from a planning/requirements pair.
---

# Task Breakdown Planner

## Purpose

Take `planning.md` and `requirements.md`, scope an MVP, break it into
implementation tasks, drive AI-assisted implementation, verify the key
scenarios, and end with a handoff. The goal isn't fast code — it's
correctly interpreting requirements, controlling scope, and clearly
handing off remaining assumptions/risks.

## Handoff (input)

Continues from `requirements-architect`, which writes
`planning-docs/{YYYY-MM-DD}_{slug}/{planning.md, requirements.md}`
(date/slug are just an example).

- Read both files first as the source of truth; if either is missing, ask
  the user for it.
- Write output to `task-workflow.md` in the same folder.

## Process

1. **Read `planning.md`** — problem, target user, goal, flow, scope/out of
   scope, risks. Restate the feature in one sentence: "이 기능은 사용자가
   ___을 혼동하지 않고 ___을 이해한 상태에서 ___할 수 있도록 돕는 UI이다."

2. **Read `requirements.md`** — page count, IA, FRs, scenarios, validation/
   error states. Decide what must be built vs. not.

3. **Propose MVP scope** — core input/output, core logic, core UI states,
   CTA enable/disable, success state, minimal error handling. Things like
   real API integration, full responsive design, animations, design tokens,
   tests, multi-page expansion can be deferred. Then call `AskUserQuestion`
   (not plain text) so the user confirms:
   1. 제안된 MVP 범위로 진행 (Recommended)
   2. 범위 조정 (포함/제외 항목 변경)

   Excluded items must still be recorded in the final handoff.

4. **Break into tasks** — implementation-order units (e.g. 화면 구조 →
   입력 상태 → 핵심 로직 → 검증/에러 → CTA/성공 상태 → 시나리오 확인 →
   handoff), not a fine-grained spec. Each task: 목적 / 구현 내용 / 완료 기준.

5. **Write the AI implementation request** for each task using: 목표 /
   입력 / 출력 / 핵심 로직 / UI 상태 (초기·정상·오류·비활성화·성공) / 제약
   (기술 스택, API 연동 여부, 스타일링 우선순위, 접근성).

6. **Review implementation output** against: 요구사항 누락 여부, 입력값
   검증, CTA 조건, 시나리오 동작, 사용자 오해를 줄이는 문구, 범위를 넘는
   임의 동작 여부, 기록되지 않은 가정 여부.

7. **Verify scenarios** from `requirements.md` — at minimum: 초기 진입,
   정상 입력, 오류 입력, CTA 비활성화/활성화, 성공 상태, 주요 토글/상태
   변경. Manual confirmation is fine under time pressure.

8. **Write the handoff** — always required; the task isn't done without it.
   구현 완료 항목 / 주요 의사결정 / 확인한 시나리오 / 구현 중 가정한 내용 /
   남은 리스크 / 다음 개선 제안.

## Output format

See [task-template.md](task-template.md):
요약 → MVP 범위 / 제외 범위 → Task List → AI 구현 요청 → 시나리오 검증 →
Handoff → Definition of Done

## Rules

- Don't implement before reading `planning.md` and `requirements.md`.
- Don't expand scope beyond requirements; don't build excluded items (e.g.
  no real API calls if integration is out of scope).
- Don't finish with only the happy path — error states must be covered.
- Never end without a handoff.
