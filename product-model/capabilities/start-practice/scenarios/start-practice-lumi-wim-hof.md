---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Start practice — lumi wim hof
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested family, existing local process and fresh remote activity determine new start, same-process
    restoration or refusal; saved configuration supplies the new run.
  kind: condition
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Phase
    - Round
    - Breath
    - Retention progress
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
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
      place: desktop-app::lumi
  actor: user
- text: A new originating Wim Hof process starts from its saved settings. Lumi origin is retained and the Product
    carries User into this practice.
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: creates
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Phase
    - Round
    - Breath
    - Retention progress
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
    to: Running
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Carry User into the newly started process
  kind: product
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
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

# Start practice — lumi wim hof

## Trigger

Start practice — lumi wim hof.

## Outcome

A new originating Wim Hof process starts from its saved settings. Lumi origin is retained and the Product carries User into this practice.
