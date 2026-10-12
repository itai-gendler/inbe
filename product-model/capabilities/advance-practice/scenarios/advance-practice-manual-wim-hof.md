---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Advance practice — manual wim hof
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: The originating live process is running at a supported manual progression point; the selected phase or movement
    position determines the next step.
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
- text: Explicit next advances Wim Hof from the current supported phase rather than waiting for its timer.
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: changes
    facts:
    - Phase
    - Round
    - Breath
    - Retention progress
    - Pause
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

# Advance practice — manual wim hof

## Trigger

Advance practice — manual wim hof.

## Outcome

Explicit next advances Wim Hof from the current supported phase rather than waiting for its timer.
