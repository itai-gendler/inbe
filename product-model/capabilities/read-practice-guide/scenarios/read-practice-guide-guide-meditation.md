---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read practice guide — guide meditation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: The selected shipped family identifies the guide presented in the same process as its configuration.
  kind: condition
  entities:
  - entity: meditation-settings
    effect: reads
    facts:
    - Duration mode
    - Custom minutes
    - Interval bell
    - Extension controls
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: The Meditation guide is presented in the same practice process as its configuration.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
references:
- kind: code
  role: implementation
  target: src/practices/practice_actions.zi
- kind: code
  role: implementation
  target: src/app/activity_start.zi
- kind: code
  role: implementation
  target: src/practices/session_results.zi
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
---

# Read practice guide — guide meditation

## Trigger

Read practice guide — guide meditation.

## Outcome

The Meditation guide is presented in the same practice process as its configuration.
