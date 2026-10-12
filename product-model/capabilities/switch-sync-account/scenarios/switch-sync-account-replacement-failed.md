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
- text: Failed replacement prevents a claimed successful switch; no stronger cross-storage rollback is promised.
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

# Switch sync account — replacement failed

## Trigger

Switch sync account for the local setup.

## Outcome

Failed replacement prevents a claimed successful switch; no stronger cross-storage rollback is promised.
