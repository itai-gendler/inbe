---
kind: primary
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
- text: A successful clearing receipt removes local setup. This observation does not certify remote retention or
    every server-side erase.
  kind: product
  entities:
  - entity: account
    effect: removes
  - entity: sync-settings
    effect: changes
    facts:
    - Enabled
    - Exchange status
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

# Clear remote data — success receipt

## Trigger

Clear remote data for the local setup.

## Outcome

A successful clearing receipt removes local setup. This observation does not certify remote retention or every server-side erase.
