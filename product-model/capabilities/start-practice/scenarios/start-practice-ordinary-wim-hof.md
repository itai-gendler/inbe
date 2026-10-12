---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Start practice — ordinary wim hof
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
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
      place: desktop-app::wim-hof
  actor: user
- text: A new originating Wim Hof process starts from its saved settings. The ordinary practice process is active.
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

# Start practice — ordinary wim hof

## Trigger

Start practice — ordinary wim hof.

## Outcome

A new originating Wim Hof process starts from its saved settings. The ordinary practice process is active.
