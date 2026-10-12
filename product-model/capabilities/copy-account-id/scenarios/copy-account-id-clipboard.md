---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Copy account id for the local setup
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The locally available public identifier supplies the clipboard text; the private key is not part of this
    copy.
  kind: condition
  entities:
  - entity: account
    effect: reads
    facts:
    - Identity
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The public identifier is placed on the native clipboard without disclosing the private key.
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

# Copy account id — clipboard

## Trigger

Copy account id for the local setup.

## Outcome

The public identifier is placed on the native clipboard without disclosing the private key.
