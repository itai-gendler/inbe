---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Clear remote data for the local setup
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The clearing confirmation precedes a request using enabled synchronization, available local credentials
    and a normalized node; local setup clears only after success.
  kind: condition
  entities:
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
- text: Cancellation sends no clearing request and retains local setup.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_sync_account_impl.zi
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
---

# Clear remote data — cancelled

## Trigger

Clear remote data for the local setup.

## Outcome

Cancellation sends no clearing request and retains local setup.
