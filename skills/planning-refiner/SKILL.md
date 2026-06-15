---
name: planning-refiner
description: Use this skill to refine early-stage product ideas, vague feature concepts, or planning notes into a structured product planning document that defines the problem, target users, goals, scope, risks, assumptions, and next steps.
---

# Planning Refiner

## Purpose

This skill transforms a rough product idea, feature concept, or planning note
into a structured product planning document that a team can align on before
writing detailed requirements.

## When to use

Use this skill when the user provides:

- A rough product idea
- A vague feature concept
- A planning memo
- Stakeholder notes
- Early-stage product direction
- Unstructured business requirements

## Process

1. **Identify the core problem.**
   - What pain point, complaint, or data point triggered this idea?
   - Is this a user problem, a business problem, or both?
   - If the input only describes a solution, work backward to find the
     problem it's meant to solve.

2. **Clarify the target user.**
   - Who specifically experiences this problem — all users, or a segment?
   - Is there a difference between who experiences the problem and who
     benefits from the fix?

3. **Define the product goal.**
   - What metric or outcome should change if this succeeds?
   - Is the goal stated as an outcome (e.g., "reduce X"), not as a feature
     (e.g., "add a button")?

4. **Separate confirmed facts from assumptions.**
   - What do we actually know vs. what are we guessing?
   - Which assumptions are risky enough that they should be validated before
     committing engineering time?

5. **Organize the proposed solution.**
   - Does the solution map directly back to the problem statement?
   - Is there a simpler version that could test the same hypothesis?

6. **Define scope and out of scope.**
   - What is the minimum needed to test the hypothesis or solve the core
     problem?
   - What adjacent requests came up that should be explicitly excluded for
     now?

7. **Identify risks, dependencies, and open questions.**
   - What could block this technically, legally, or organizationally?
   - What needs a stakeholder's input before work can proceed?

8. **Produce a structured planning document.**
   - Could someone unfamiliar with the original note understand the plan on
     its own?
   - Use [templates/planning-template.md](../../templates/planning-template.md)
     as the output structure.

## Output format

See [templates/planning-template.md](../../templates/planning-template.md)
for the full structure:

1. Summary
2. Problem Statement
3. Target User
4. Product Goal
5. Proposed Solution
6. Scope
7. Out of Scope
8. Assumptions
9. Risks
10. Open Questions
11. Next Steps

## Example

- [examples/input.md](examples/input.md) — a one-line rough idea
- [examples/output.md](examples/output.md) — the resulting structured plan

The plan's "Next Steps" section hands off directly to
`requirements-architect`, whose example input is this plan's output.
