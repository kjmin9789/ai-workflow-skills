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

1. Understand the product objective.
2. Identify users and use cases.
3. Define functional requirements.
4. Define non-functional requirements.
5. Write user stories when useful.
6. Add acceptance criteria.
7. Identify edge cases and constraints.
8. List dependencies and unresolved questions.

## Output format

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

### Input (plan from `planning-refiner`)

> Goal: Reduce notification opt-out rate by giving users granular control
> over notification categories. Add a "Notification Settings" screen with
> per-category toggles (comments, likes, mentions, marketing). Existing
> users default to all categories on.

### Output (requirements, abbreviated)

**1. Overview**
Add a per-category notification settings screen, replacing the single global
push notification toggle.

**2. Users and Use Cases**
- Active user who wants to mute "likes" but keep "comments" and "mentions"
- New user configuring notification preferences during onboarding

**3. Functional Requirements**
- FR1: Display a "Notification Settings" screen listing categories: Comments,
  Likes, Mentions, Marketing
- FR2: Each category has an independent on/off toggle
- FR3: Toggling a category immediately persists the preference to the backend
- FR4: Existing users are migrated with all categories set to "on" to match
  current behavior
- FR5: New users see Marketing defaulted to "off"

**4. Non-Functional Requirements**
- NFR1: Preference changes must be reflected in notification delivery within
  5 minutes
- NFR2: Settings screen must load in under 500ms on a cached profile

**5. User Stories**
- As an active user, I want to turn off "Likes" notifications so that I
  receive fewer interruptions while keeping important alerts.
- As a new user, I want marketing notifications off by default so that I'm
  not opted into promotional messages without choosing to.

**6. Acceptance Criteria**
- Given a user turns off "Likes", when a like event occurs, then no push
  notification is sent for that event to that user
- Given an existing user opens the settings screen for the first time, then
  all categories appear as "on"
- Given a new user signs up, then "Marketing" appears as "off" by default

**7. Edge Cases**
- User disables all categories — confirm this is allowed (no forced minimum)
- Notification event maps to multiple categories — define priority/ownership
- User toggles a setting while offline — handle retry/sync on reconnect

**8. Dependencies**
- Backend notification service must support category-based filtering
- Migration script for existing user preference records

**9. Constraints**
- Must ship within the existing notification settings UI shell (no new nav
  entry point)

**10. Open Questions**
- Final category list and naming — confirm with backend before implementation
- Should "Mentions" be a non-disableable category for safety-critical alerts?

---

This output is ready to be passed to `task-breakdown-planner` to generate a
trackable task list.
