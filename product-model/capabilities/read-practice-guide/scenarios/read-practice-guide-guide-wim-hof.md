---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read practice guide — guide wim hof
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: The selected shipped family identifies the guide presented in the same process as its configuration.
  kind: condition
  entities:
  - entity: wim-hof-settings
    effect: reads
    facts:
    - Rounds
    - Breaths
    - Speed
    - Progression
    - Start preference
    - Between-round pause
    - Animation
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: The Wim Hof guide is presented in the same practice process as its configuration.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
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
  target: src/practices/whm/whm_session.zi
---

# Read practice guide — guide wim hof

## Trigger

Read practice guide — guide wim hof.

## Outcome

The Wim Hof guide is presented in the same practice process as its configuration.
