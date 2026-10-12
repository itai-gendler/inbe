---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Keep local data for pending current-identity changes
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Current-identity incoming data is retained for review; the local record values are preserved when the pending
    decision is dismissed.
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
- text: Pending incoming review is dismissed and local record values remain.
  kind: product
  entities:
  - entity: sync-settings
    effect: changes
    facts:
    - Pending review
    - Exchange status
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

# Keep local data — pending dismissed

## Trigger

Keep local data for pending current-identity changes.

## Outcome

Pending incoming review is dismissed and local record values remain.
