---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Replace local data for pending current-identity changes
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: A current-identity pending response is present; replacement clears the implemented SQL data scope before
    applying the snapshot within its savepoint.
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

# Replace local data — apply failed

## Trigger

Replace local data for pending current-identity changes.

## Outcome

Failed apply reports failure without claiming completed merge or replacement; only the implemented transaction scope is atomic.
