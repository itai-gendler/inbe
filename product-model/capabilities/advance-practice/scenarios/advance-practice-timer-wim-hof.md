---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: The originating live timer reaches the next breath, phase, movement or duration boundary
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
  unattended: true
- text: Breaths and timed retention advance through the configured round sequence.
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

# Advance practice — timer wim hof

## Trigger

Advance practice — timer wim hof.

## Outcome

Breaths and timed retention advance through the configured round sequence.
