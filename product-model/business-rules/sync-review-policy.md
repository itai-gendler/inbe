---
appliesTo:
- type: entity
  id: sync-settings
- type: entity
  id: habit
- type: entity
  id: habit-day
- type: entity
  id: wim-hof-session
- type: entity
  id: meditation-session
- type: entity
  id: patterns-session
- type: entity
  id: sun-salutation-session
references:
- kind: code
  role: implementation
  target: src/app/app_sync.zi
- kind: code
  role: implementation
  target: src/app/sync_retry.zi
- kind: code
  role: implementation
  target: src/storage/sync_review.zi
---

# Incoming review follows actual auto-apply predicates

Auto-review considers local/outbox state, small session changes at most two, and implemented activity identifiers 0,1,2. Patterns activity 3 can trigger unknown-activity review. Keep dismisses, merge uses conflict paths, replace uses replacement scope.
