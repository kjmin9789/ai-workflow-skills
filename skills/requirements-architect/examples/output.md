# Output

Requirements produced from [input.md](input.md), following
[../requirements-template.md](../requirements-template.md).

## 1. Overview
Add a per-category notification settings screen, replacing the single global
push notification toggle.

## 2. Users and Use Cases
- Active user who wants to mute "Likes" but keep "Comments" and "Mentions"
- New user configuring notification preferences during onboarding

## 3. Functional Requirements
- FR1: Display a "Notification Settings" screen listing categories: Comments,
  Likes, Mentions, Marketing
- FR2: Each category has an independent on/off toggle
- FR3: Toggling a category immediately persists the preference to the backend
- FR4: Existing users are migrated with all categories set to "on" to match
  current behavior
- FR5: New users see Marketing defaulted to "off"

## 4. Non-Functional Requirements
- NFR1: Preference changes must be reflected in notification delivery within
  5 minutes
- NFR2: Settings screen must load in under 500ms on a cached profile

## 5. User Stories
- As an active user, I want to turn off "Likes" notifications so that I
  receive fewer interruptions while keeping important alerts.
- As a new user, I want marketing notifications off by default so that I'm
  not opted into promotional messages without choosing to.

## 6. Acceptance Criteria
- Given a user turns off "Likes", when a like event occurs, then no push
  notification is sent for that event to that user
- Given an existing user opens the settings screen for the first time, then
  all categories appear as "on"
- Given a new user signs up, then "Marketing" appears as "off" by default

## 7. Edge Cases
- User disables all categories — confirm this is allowed (no forced minimum)
- Notification event maps to multiple categories — define priority/ownership
- User toggles a setting while offline — handle retry/sync on reconnect

## 8. Dependencies
- Backend notification service must support category-based filtering
- Migration script for existing user preference records

## 9. Constraints
- Must ship within the existing notification settings UI shell (no new nav
  entry point)

## 10. Open Questions
- Final category list and naming — confirm with backend before implementation
- Should "Mentions" be a non-disableable category for safety-critical alerts?
