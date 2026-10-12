---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Start practice — lumi other active
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: A different local practice is already active; the requested Lumi family is not that existing process.
  kind: condition
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: apps-settings
    effect: reads
    facts:
    - Practices available
  - entity: account
    effect: reads
    facts:
    - Identity
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: A different local live practice prevents starting the requested Lumi practice.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
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
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Start practice — lumi other active

## Trigger

Start practice — lumi other active.

## Outcome

A different local live practice prevents starting the requested Lumi practice.
