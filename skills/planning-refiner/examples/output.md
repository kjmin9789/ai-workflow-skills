# Output

Structured plan produced from [input.md](input.md), following
[../../../templates/planning-template.md](../../../templates/planning-template.md).

## 1. Summary
Replace the current single on/off notification toggle with per-category
notification settings so users can reduce notification fatigue.

## 2. Problem Statement
Users are receiving too many notifications and have no way to turn off
specific types, leading to complaints and increased app uninstalls.

## 3. Target User
Active users who have notifications enabled but mute the app at the OS level
due to volume.

## 4. Product Goal
Reduce notification opt-out rate by giving users granular control over
notification categories.

## 5. Proposed Solution
Add a "Notification Settings" screen with per-category toggles (e.g.,
comments, likes, mentions, marketing) instead of a single global switch.

## 6. Scope
- New notification settings screen
- Per-category toggle for push notifications
- Default values for existing users (opt-in to all, matching current behavior)

## 7. Out of Scope
- Email/SMS notification preferences
- Notification scheduling (quiet hours)

## 8. Assumptions
- Existing notification events can be mapped to a fixed set of categories
- Backend can filter notification sends by category per user

## 9. Risks
- Backend notification service may not support per-category filtering today
- Migration of existing user preferences needs a safe default

## 10. Open Questions
- How many categories should we launch with?
- Should marketing notifications default to off for new users (compliance)?

## 11. Next Steps
- Pass this plan to `requirements-architect` to define detailed requirements
- Confirm category list with backend team
