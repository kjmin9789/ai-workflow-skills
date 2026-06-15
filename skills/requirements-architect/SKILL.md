---
name: requirements-architect
description: Use this skill to transform product plans or feature concepts into implementation-ready requirements, including functional requirements, non-functional requirements, user stories, acceptance criteria, edge cases, dependencies, and unresolved questions.
---

# Requirements Architect

## Purpose

This skill converts a product plan, feature concept, or business objective
into structured requirements that product, design, engineering, QA, and
operations teams can build against.

## When to use

Use this skill when the user provides:

- A product plan (e.g., the output of `planning-refiner`)
- A feature concept
- A business objective
- A planning document
- User needs
- Stakeholder requests

## Process

1. **Understand the product objective.**
   - What does the plan say success looks like?
   - Re-read the goal and scope before writing any requirement — every
     requirement should trace back to one of them.

2. **Identify users and use cases.**
   - List concrete scenarios ("a user mutes Likes but keeps Comments"), not
     just abstract personas.
   - Does each use case map to at least one requirement below?

3. **Define functional requirements.**
   - Is each requirement specific and testable (not "support notifications"
     but "user can toggle each category independently")?
   - Number them (FR1, FR2, ...) for traceability into tasks and tests.

4. **Define non-functional requirements.**
   - Which of performance, reliability, security, privacy, or compliance
     actually applies to this feature?
   - Avoid boilerplate NFRs that don't reflect a real constraint of this
     feature.

5. **Write user stories when useful.**
   - Use "As a [user], I want [goal] so that [benefit]."
   - Skip this for purely technical/internal requirements where a story adds
     no clarity.

6. **Add acceptance criteria.**
   - Use "Given [context], when [action], then [outcome]."
   - Does every major functional requirement have at least one acceptance
     criterion, including one negative or edge-case scenario?

7. **Identify edge cases and constraints.**
   - What happens at the boundaries — zero selected, all selected, offline,
     conflicting states, migration of existing data?
   - What constraints (UI shell, existing APIs, timeline) limit the solution
     space?

8. **List dependencies and unresolved questions.**
   - What does engineering need confirmed before they can estimate this work?
   - Use [templates/requirements-template.md](../../templates/requirements-template.md)
     as the output structure.

## Output format

See [templates/requirements-template.md](../../templates/requirements-template.md)
for the full structure:

1. Overview
2. Users and Use Cases
3. Functional Requirements
4. Non-Functional Requirements
5. User Stories
6. Acceptance Criteria
7. Edge Cases
8. Dependencies
9. Constraints
10. Open Questions

## Example

- [examples/input.md](examples/input.md) — the plan from `planning-refiner`
- [examples/output.md](examples/output.md) — the resulting requirements

This output is ready to be passed to `task-breakdown-planner`, whose example
input is these requirements.
