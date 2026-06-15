---
name: task-breakdown-planner
description: Use this skill to decompose product requirements or feature specifications into clear, trackable tasks across design, engineering, QA, analytics, release, and operations workflows.
---

# Task Breakdown Planner

## Purpose

This skill breaks product requirements or feature specifications into
actionable tasks that can be tracked by product, design, engineering, QA,
analytics, release, and operations teams.

## When to use

Use this skill when the user provides:

- Product requirements (e.g., the output of `requirements-architect`)
- Feature specifications
- User stories
- Acceptance criteria
- Planning documents
- Implementation goals

## Process

1. **Understand the requirement or feature scope.**
   - Read all functional and non-functional requirements and acceptance
     criteria before splitting work — tasks created from a partial read
     tend to miss dependencies.

2. **Identify workstreams.**
   - Which teams/functions are involved (backend, frontend, QA, analytics,
     design, release)?
   - Don't create a workstream with no tasks, and don't force every feature
     into the same fixed set of workstreams.

3. **Break the work into actionable tasks.**
   - Can this task be completed and verified independently?
   - Is it small enough that "done" is unambiguous?

4. **Assign each task to a functional area.**
   - Does each task have exactly one owner/team — not "backend & frontend"?

5. **Identify dependencies.**
   - Which tasks block others, and in which direction?
   - Are cross-team dependencies called out explicitly (not just implied by
     ordering)?

6. **Define deliverables.**
   - Is the deliverable a concrete artifact (a script, a deployed endpoint, a
     test report) rather than a vague "work on X"?

7. **Highlight risks and blockers.**
   - What could delay or derail this — high-traffic systems, migrations,
     external approvals?

8. **Suggest a practical execution order.**
   - Does the order respect the dependencies identified above, with the
     critical path first?
   - Use [templates/task-template.md](../../templates/task-template.md) as
     the output structure.

## Output format

See [templates/task-template.md](../../templates/task-template.md) for the
full structure:

1. Summary
2. Workstreams
3. Task List
4. Dependencies
5. Risks and Blockers
6. Suggested Execution Order
7. Definition of Done

### Task format

```text
- Task:
- Owner:
- Description:
- Dependency:
- Deliverable:
- Priority:
```

## Example

- [examples/input.md](examples/input.md) — the requirements from
  `requirements-architect`
- [examples/output.md](examples/output.md) — the resulting task breakdown
