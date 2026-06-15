---
name: planning-refiner
description: Decide the right user flow, define the required pages, clarify each page's purpose, and turn the plan into actionable tasks.
---

# Planning Refiner

## Purpose

Turn a rough product idea into a concise planning document.

Focus only on:

```text
Problem → Flow Options → Selected Flow → Page Count → Pages → Tasks
```

Do not produce a general planning doc (no long problem statements, scope,
risks, or proposed-solution essays). Keep everything short.

## Language

Match the user's language.

For Korean input, write the final `planning.md` primarily in Korean. Use
Korean section titles with short English labels for structure and agent
readability (e.g., "대상과 문제 / Target & Problem").

Do not create separate Korean and English versions unless the user
explicitly asks.

## Process

1. Understand the target and problem from the rough idea.
2. If the direction is unclear, ask **one** focused question before
   producing anything — see "Interview format" below.
3. Present 2–4 flow options for the user to choose from.
4. Ask the user to pick a flow if it isn't obvious from context.
5. Recommend a page count for the selected flow, with a reason.
6. For each page, define its purpose, user action, CTA, and metric.
   `Purpose` is the most important column — explain *why* the page exists
   in one short sentence.
7. Turn the page plan directly into tasks. Tasks replace "Next Steps" — there
   is no separate next-steps section.
8. If real data isn't available, use mock data — clearly labeled as mock,
   and varied across scenarios (different target users, flow choices, page
   counts, task breakdowns) rather than presented as if it were real
   evidence.
9. Produce one final `planning.md` using
   [../../templates/planning-final-template.md](../../templates/planning-final-template.md).

## Interview format

When the direction is unclear, ask exactly one question at a time, in this
format:

```text
HYPOTHESIS:
CONFIDENCE:
Q:
GUESS:
```

Never ask multiple questions in one turn.

## Required tables

**Flow options:**

| Option | Flow | Why | Tradeoff |
|---|---|---|---|

**Pages:**

| Step | Page | Purpose | User Action | CTA | Metric |
|---:|---|---|---|---|---|

**Tasks:**

| Task ID | Task | Owner | Priority | Acceptance Criteria |
|---|---|---|---|---|

Tasks must be specific enough to hand off to product, design, engineering,
data, or QA without further clarification.

## Example (inline, abbreviated)

Input: "알림 설정 화면을 새로 만들고 싶어요."

- Flow Options: (A) 설정 탭 안에 알림 설정 진입점 추가, (B) 온보딩 중 알림
  설정 선택 단계 추가, (C) 둘 다 — 표로 Why/Tradeoff 정리
- Selected Flow: (A) 설정 탭 진입
- Page Count: 1 page — 단일 설정 화면으로 충분
- Pages: `| 1 | 알림 설정 화면 | 카테고리별 알림 on/off 제어 | 토글 클릭 |
  (없음) | 카테고리별 opt-out 비율 |`
- Tasks: `| T1 | 알림 설정 화면 UI 구현 | Frontend | High | 카테고리별
  토글이 표시되고 즉시 저장됨 |`

## Final output

Create one file:

```text
planning-docs/{YYYY-MM-DD}_{slug}/planning.md
```

Do not create separate input/output files unless the user asks.
