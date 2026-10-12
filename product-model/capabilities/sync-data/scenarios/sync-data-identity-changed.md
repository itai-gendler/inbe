---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: The local identity changes while an exchange response is in flight
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
- text: An in-flight response after local identity change is abandoned rather than applied to the new context.
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

# Sync data — identity changed

## Trigger

Sync data for pending current-identity changes.

## Outcome

An in-flight response after local identity change is abandoned rather than applied to the new context.
