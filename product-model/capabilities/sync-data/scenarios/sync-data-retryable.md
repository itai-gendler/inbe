---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: The current exchange attempt returns a retryable challenge, authentication, request or payload classification
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
- text: Challenge/authentication, request and other retryable classifications schedule a fresh attempt at 5, 15,
    30 then 60 seconds; authentication can renew its challenge. Eligible transport failures may advance to another
    node.
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

# Sync data — retryable

## Trigger

Sync data for pending current-identity changes.

## Outcome

Challenge/authentication, request and other retryable classifications schedule a fresh attempt at 5, 15, 30 then 60 seconds; authentication can renew its challenge. Eligible transport failures may advance to another node.
