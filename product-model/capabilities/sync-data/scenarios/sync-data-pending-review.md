---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Sync data for pending current-identity changes
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Enabled synchronization and current request identity precede protocol-v6 exchange; response shape and auto-apply
    predicates select ordinary apply or pending review.
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
- text: A response outside auto-apply predicates is retained for review; imported session changes above the threshold
    or activity values outside the implemented set can require the decision.
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

# Sync data — pending review

## Trigger

Sync data for pending current-identity changes.

## Outcome

A response outside auto-apply predicates is retained for review; imported session changes above the threshold or activity values outside the implemented set can require the decision.
