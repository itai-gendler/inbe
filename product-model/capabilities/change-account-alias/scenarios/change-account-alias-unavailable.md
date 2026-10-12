---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Change account alias for the local setup
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The entered alias is normalized by removing @ and lowercasing, then checked for four through thirty-two
    alphanumeric or underscore characters before registration.
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
- text: Unavailable registration reports status and does not claim that the alias was registered.
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

# Change account alias — unavailable

## Trigger

Change account alias for the local setup.

## Outcome

Unavailable registration reports status and does not claim that the alias was registered.
