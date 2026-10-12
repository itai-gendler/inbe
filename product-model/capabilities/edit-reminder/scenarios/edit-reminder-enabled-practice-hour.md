---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Edit reminder at the selected entry position
  kind: actor
  entities:
  - entity: reminder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
- text: The selected entry position exists; enabled state, one of four practices and hour zero through twenty-three
    identify its valid saved values.
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
- text: The selected valid entry immediately saves enabled state, one of four practices and hour zero through twenty-three.
  kind: product
  entities:
  - entity: reminder
    effect: changes
    facts:
    - Practice
    - Enabled
    - Hour
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Edit reminder — enabled practice hour

## Trigger

Edit reminder at the selected entry position.

## Outcome

The selected valid entry immediately saves enabled state, one of four practices and hour zero through twenty-three.
