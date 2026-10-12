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
- text: The proposed identity becomes installed and exchange can be requested. Replacement clears the implemented
    session/Habit/List/Todo/social snapshot/outbox scope; Diary and Lumi cell records and all settings are
    not claimed cleared.
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
  - entity: habit
    effect: removes
  - entity: habit-day
    effect: removes
    with: habit
  - entity: list
    effect: removes
  - entity: todo
    effect: removes
    with: list
    from: Incomplete
    as: incomplete-items
  - entity: todo
    effect: removes
    with: list
    from: Complete
    as: complete-items
  - entity: wim-hof-session
    effect: removes
  - entity: meditation-session
    effect: removes
  - entity: patterns-session
    effect: removes
  - entity: sun-salutation-session
    effect: removes
  - entity: profile
    effect: changes
    facts:
    - Account access mode
  - entity: friend
    effect: removes
  - entity: friend-request
    effect: removes
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
- kind: code
  role: implementation
  target: src/storage/storage_core.zi#storage_clear_local_sync_data
---

# Switch sync account — replace local

## Trigger

Switch sync account for the local setup.

## Outcome

The proposed identity becomes installed and exchange can be requested. Replacement clears the implemented session/Habit/List/Todo/social snapshot/outbox scope; Diary and Lumi cell records and all settings are not claimed cleared.
