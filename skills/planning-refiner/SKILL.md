---
name: planning-refiner
description: Clarify a rough product idea through targeted questions, decide the right user flow, and turn it into a concise planning document.
---

# Planning Refiner

## Purpose

Turn a rough product idea into a concise planning document.

Focus only on:

```text
Problem → Flow Options → Selected Flow → Scope → Risks / Open Questions
```

Do not pad the document with long essays. Keep every section short.

## Language

Match the user's language. For Korean input, write the final `planning.md`
in Korean.

Do not create separate Korean and English versions unless the user
explicitly asks.

## Process

1. Understand the target and problem from the rough idea.
2. Run the **clarification loop** (see below) until confidence reaches 90%
   and there are no logical gaps — do not produce any output before this.
3. Present 2–4 flow options for the user to choose from.
4. Ask the user to pick a flow if it isn't obvious from context.
5. Summarize the selected flow's scope and what's explicitly excluded.
6. List risks and anything that still needs confirmation.
7. Produce one final `planning.md` using
   [../../templates/planning-final-template.md](../../templates/planning-final-template.md).

## Clarification loop

Before presenting flow options, the goal, target user, and problem must be
clear enough that no part of the plan relies on a logical leap.

1. Form a hypothesis about the goal, target user, and problem.
2. Estimate `CONFIDENCE` (0–100%) that this hypothesis is correct and
   complete enough to plan from.
3. If `CONFIDENCE < 90%`, ask **exactly one** question that would close the
   biggest gap — see "Interview format" below.
4. Update the hypothesis and confidence based on the user's answer.
5. Repeat steps 1–4 until `CONFIDENCE >= 90%`.
6. Once `CONFIDENCE >= 90%`, restate the final hypothesis in one short line
   for the user to confirm, then proceed to flow options.

Never skip ahead to flow options while confidence is below 90% or a logical
gap remains unresolved.

## Interview format

While in the clarification loop, ask exactly one question at a time, in this
format:

```text
HYPOTHESIS:
CONFIDENCE:
Q:
GUESS:
```

- `HYPOTHESIS`: current best understanding of the goal/target/problem
- `CONFIDENCE`: current confidence (0–100%) in that hypothesis
- `Q`: the single question that most reduces uncertainty
- `GUESS`: your best guess at the answer, so the user can simply confirm or
  correct it

Never ask multiple questions in one turn.

## Output format

Return the planning document in Korean using the following structure:

1. 요약 / Summary
2. 문제 정의 / Problem
3. 대상 사용자 / Target User
4. 목표 / Goal
5. 플로우 옵션 / Flow Options
6. 선택한 방향 / Selected Flow
7. 범위 / 제외 범위 / Scope / Out of Scope
8. 리스크 및 확인 필요 사항 / Risks & Open Questions

See [../../templates/planning-final-template.md](../../templates/planning-final-template.md).

## Final output

Create one file:

```text
planning-docs/{YYYY-MM-DD}_{slug}/planning.md
```

Do not create separate input/output files unless the user asks.
