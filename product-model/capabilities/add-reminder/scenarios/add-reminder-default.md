---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Add reminder at the selected entry position
  kind: actor
  entities:
  - entity: reminder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
- text: The saved reminder entries contain fewer than sixteen positions before another entry is added.
  kind: condition
  entities:
  - entity: reminder
    effect: reads
    facts:
    - Entry position
    - Practice
    - Enabled
    - Hour
    - Last day
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
- text: A default enabled Wim Hof reminder at hour eight is saved with last-day bookkeeping initially zero.
  kind: product
  entities:
  - entity: reminder
    effect: creates
    facts:
    - Entry position
    - Practice
    - Enabled
    - Hour
    - Last day
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Add reminder — default

## Trigger

Add reminder at the selected entry position.

## Outcome

A default enabled Wim Hof reminder at hour eight is saved with last-day bookkeeping initially zero.
