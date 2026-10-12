---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Switch sync account for the local setup
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Different credentials are retained as a proposed switch; preserve, replace or cancel decides the installed
    identity and the implemented local-data scope.
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
- text: Cancellation leaves the current installed identity and local data intact.
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

# Switch sync account — cancelled

## Trigger

Switch sync account for the local setup.

## Outcome

Cancellation leaves the current installed identity and local data intact.
