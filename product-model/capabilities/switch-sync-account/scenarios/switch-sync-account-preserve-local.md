---
kind: primary
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
- text: The proposed identity becomes installed and exchange can be requested. Demonstrated local data is retained
    through the preserve choice.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Identity
    - Private key
    - Installed identity
    - Proposed identity
  - entity: sync-settings
    effect: changes
    facts:
    - Enabled
    - Exchange status
  - entity: profile
    effect: changes
    facts:
    - Account access mode
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

# Switch sync account — preserve local

## Trigger

Switch sync account for the local setup.

## Outcome

The proposed identity becomes installed and exchange can be requested. Demonstrated local data is retained through the preserve choice.
