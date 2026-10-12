---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Export account key for the local setup
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The available local account-key credentials supply the plaintext backup selected through the native file
    picker.
  kind: condition
  entities:
  - entity: account
    effect: reads
    facts:
    - Identity
    - Private key
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The native picker writes the exposed plaintext key backup; this is not the encrypted-helper contract.
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

# Export account key — plaintext file

## Trigger

Export account key for the local setup.

## Outcome

The native picker writes the exposed plaintext key backup; this is not the encrypted-helper contract.
