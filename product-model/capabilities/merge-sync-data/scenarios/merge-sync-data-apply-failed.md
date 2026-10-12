---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Merge sync data for pending current-identity changes
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: A current-identity pending response is present; merge retains local outbox work and uses the implemented
    record ordering and equal-time conflict checks.
  kind: condition
  entities:
  - entity: sync-settings
    effect: reads
    facts:
    - Enabled
    - Exchange status
    - Retry status
    - Pending review
  - entity: account
    effect: reads
    facts:
    - Identity
    - Alias
    - Proposed identity
    - Installed identity
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Failed apply reports failure without claiming completed merge or replacement; only the implemented transaction
    scope is atomic.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
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
- kind: code
  role: implementation
  target: src/storage/storage_core.zi
---

# Merge sync data — apply failed

## Trigger

Merge sync data for pending current-identity changes.

## Outcome

Failed apply reports failure without claiming completed merge or replacement; only the implemented transaction scope is atomic.
