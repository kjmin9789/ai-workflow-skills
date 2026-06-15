# Output

Task breakdown produced from [input.md](input.md), following
[../../../templates/task-template.md](../../../templates/task-template.md).

## 1. Summary
Implementation plan for the per-category notification settings feature,
covering backend filtering support, UI, migration, and QA.

## 2. Workstreams
- Backend (notification service)
- Mobile/Frontend (settings UI)
- Data migration
- QA
- Analytics

## 3. Task List

- Task: Add category field to notification event schema
  - Owner: Backend
  - Description: Extend the notification event model so each event carries
    a category (comments, likes, mentions, marketing)
  - Dependency: None
  - Deliverable: Updated schema + API docs
  - Priority: High

- Task: Implement category-based filtering in notification dispatcher
  - Owner: Backend
  - Description: Dispatcher checks the user's per-category preference before
    sending a push notification
  - Dependency: Category field on notification events
  - Deliverable: Filtering logic deployed behind a feature flag
  - Priority: High

- Task: Build Notification Settings screen
  - Owner: Frontend
  - Description: New screen listing categories with toggles, wired to the
    preferences API
  - Dependency: Preferences API contract finalized
  - Deliverable: Settings screen in app, behind feature flag
  - Priority: High

- Task: Write migration script for existing user preferences
  - Owner: Backend
  - Description: Backfill all existing users with every category set to "on"
  - Dependency: Preferences storage schema
  - Deliverable: Migration script + rollback plan
  - Priority: Medium

- Task: Set default preferences for new users
  - Owner: Backend
  - Description: New user signup flow sets Marketing to "off", all other
    categories "on"
  - Dependency: Preferences storage schema
  - Deliverable: Updated signup flow
  - Priority: Medium

- Task: QA test plan for category filtering and defaults
  - Owner: QA
  - Description: Verify toggles persist, filtering works per category, and
    default values are correct for new vs. existing users
  - Dependency: Settings screen + filtering logic deployed to staging
  - Deliverable: Test plan + executed results
  - Priority: High

- Task: Add analytics events for toggle usage
  - Owner: Analytics
  - Description: Track which categories users disable most, to inform
    future notification strategy
  - Dependency: Settings screen
  - Deliverable: Event tracking spec + dashboard
  - Priority: Low

## 4. Dependencies
- Frontend settings screen depends on the finalized preferences API
- Migration script depends on the finalized preferences storage schema
- QA depends on both backend filtering and frontend UI being deployed to
  staging

## 5. Risks and Blockers
- Notification dispatcher changes touch a high-traffic system — needs a
  feature flag and staged rollout
- Migration must run before the new settings screen is enabled, or existing
  users could see incorrect defaults

## 6. Suggested Execution Order
1. Add category field to notification event schema
2. Implement category-based filtering in dispatcher (behind feature flag)
3. Run migration script for existing users
4. Set defaults for new users
5. Build Notification Settings screen
6. QA pass across both new and existing user scenarios
7. Add analytics events
8. Roll out feature flag

## 7. Definition of Done
- Users can independently toggle each notification category and see the
  change reflected in delivered notifications within 5 minutes
- Existing users retain their current notification behavior after migration
- New users see Marketing notifications off by default
- QA test plan passed and analytics events are firing in production
