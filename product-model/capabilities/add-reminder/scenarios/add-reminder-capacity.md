---
kind: validation
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
- text: Sixteen saved reminder entries already occupy the native capacity.
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
- text: At sixteen entries, another native reminder is refused.
  kind: product
  entities:
  - entity: reminder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Add reminder — capacity

## Trigger

Add reminder at the selected entry position.

## Outcome

At sixteen entries, another native reminder is refused.
