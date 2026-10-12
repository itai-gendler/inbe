---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Remove reminder at the selected entry position
  kind: actor
  entities:
  - entity: reminder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
- text: The selected saved entry position exists before removal and persistence of the remaining reminder positions.
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
- text: The selected entry is removed and remaining positions are saved.
  kind: product
  entities:
  - entity: reminder
    effect: removes
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Remove reminder — entry

## Trigger

Remove reminder at the selected entry position.

## Outcome

The selected entry is removed and remaining positions are saved.
