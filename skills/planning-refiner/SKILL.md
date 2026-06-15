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

1. Identify the core problem.
2. Clarify the target user.
3. Define the product goal.
4. Separate confirmed facts from assumptions.
5. Organize the proposed solution.
6. Define scope and out of scope.
7. Identify risks, dependencies, and open questions.
8. Produce a structured planning document.

## Output format

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

### Input (rough idea)

> "유저들이 알림이 너무 많이 온다는 불만이 많아요. 알림 설정을 더 세분화해서
> 원하는 알림만 받을 수 있게 하면 좋을 것 같아요."

### Output (structured plan, abbreviated)

**1. Summary**
Replace the current single on/off notification toggle with per-category
notification settings so users can reduce notification fatigue.

**2. Problem Statement**
Users are receiving too many notifications and have no way to turn off
specific types, leading to complaints and increased app uninstalls.

**3. Target User**
Active users who have notifications enabled but mute the app at the OS level
due to volume.

**4. Product Goal**
Reduce notification opt-out rate by giving users granular control over
notification categories.

**5. Proposed Solution**
Add a "Notification Settings" screen with per-category toggles (e.g.,
comments, likes, mentions, marketing) instead of a single global switch.

**6. Scope**
- New notification settings screen
- Per-category toggle for push notifications
- Default values for existing users (opt-in to all, matching current behavior)

**7. Out of Scope**
- Email/SMS notification preferences
- Notification scheduling (quiet hours)

**8. Assumptions**
- Existing notification events can be mapped to a fixed set of categories
- Backend can filter notification sends by category per user

**9. Risks**
- Backend notification service may not support per-category filtering today
- Migration of existing user preferences needs a safe default

**10. Open Questions**
- How many categories should we launch with?
- Should marketing notifications default to off for new users (compliance)?

**11. Next Steps**
- Pass this plan to `requirements-architect` to define detailed requirements
- Confirm category list with backend team
