---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: The current exchange attempt returns an unknown or actionable classification that stops automatic retry
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
    - Private key
    - Alias
    - Proposed identity
    - Installed identity
  contexts:
    desktop:
      place: desktop-app
  unattended: true
- text: Unknown or actionable failure stops automatic retry and exposes status for local action.
  kind: product
  entities:
  - entity: sync-settings
    effect: changes
    facts:
    - Exchange status
    - Retry status
    - Pending review
  contexts:
    desktop:
      place: desktop-app::account
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

# Sync data — actionable

## Trigger

Sync data for pending current-identity changes.

## Outcome

Unknown or actionable failure stops automatic retry and exposes status for local action.
