---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Log out for the local setup
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The current local credential setup is identified for removal; synchronization is disabled while local product
    records remain.
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
- text: Local alias/token/key setup is removed and synchronization disabled; local records remain.
  kind: product
  entities:
  - entity: account
    effect: removes
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

# Log out — local setup

## Trigger

Log out for the local setup.

## Outcome

Local alias/token/key setup is removed and synchronization disabled; local records remain.
