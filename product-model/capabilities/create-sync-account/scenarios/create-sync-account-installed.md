---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Create sync account for the local setup
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Current credentials and existing practice/Habit data determine whether generated credentials install immediately
    or await preserve-or-replace confirmation.
  kind: condition
  entities:
  - entity: account
    effect: reads
    facts:
    - Identity
    - Alias
    - Proposed identity
    - Installed identity
  - entity: habit
    effect: reads
    facts:
    - Identity
  - entity: habit-day
    effect: reads
    facts:
    - Stored count
    - Stored completion
  - entity: wim-hof-session
    effect: reads
    facts:
    - Identity
  - entity: meditation-session
    effect: reads
    facts:
    - Identity
  - entity: patterns-session
    effect: reads
    facts:
    - Identity
  - entity: sun-salutation-session
    effect: reads
    facts:
    - Identity
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: New credentials are installed locally. Creation does not itself promise that enabled synchronization is
    immediately set.
  kind: product
  entities:
  - entity: account
    effect: creates
    facts:
    - Identity
    - Private key
    - Alias
    - Proposed identity
    - Installed identity
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

# Create sync account — installed

## Trigger

Create sync account for the local setup.

## Outcome

New credentials are installed locally. Creation does not itself promise that enabled synchronization is immediately set.
