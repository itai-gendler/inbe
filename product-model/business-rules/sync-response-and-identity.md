---
appliesTo:
- type: entity
  id: account
- type: entity
  id: sync-settings
- type: entity
  id: habit
- type: entity
  id: habit-day
- type: entity
  id: list
- type: entity
  id: todo
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

# Synchronization applies only the current protocol and request identity

Protocol v6 authentication and current-request identity guard application. Ordinary apply/ack is transactional; alias/seen-version metadata can update outside it. Authentication validity is not a verified human role.
