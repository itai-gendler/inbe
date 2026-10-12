---
kind: edge
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
- text: Credential generation or setup failure is reported without claiming installation.
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

# Create sync account — creation failed

## Trigger

Create sync account for the local setup.

## Outcome

Credential generation or setup failure is reported without claiming installation.
