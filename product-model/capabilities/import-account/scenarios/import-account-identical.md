---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Import account for the local setup
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The imported valid credentials equal the installed account identity, so the identity and local records are
    not reset.
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
- text: Identical account credentials are accepted without clearing data or restarting the identity switch.
  kind: product
  entities:
  - entity: account
    effect: reads
    facts: []
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

# Import account — identical

## Trigger

Import account for the local setup.

## Outcome

Identical account credentials are accepted without clearing data or restarting the identity switch.
