---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Finish practice — wim hof save failed
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: The originating process has qualifying recorded progress and reaches ordinary completion or explicit Finish
    from awaiting finish.
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
- text: Wim Hof save failure can return through app initialization without retaining one uniform recoverable result;
    no durable saved result is claimed.
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: removes
    from: Running
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

# Finish practice — wim hof save failed

## Trigger

Finish practice — wim hof save failed.

## Outcome

Wim Hof save failure can return through app initialization without retaining one uniform recoverable result; no durable saved result is claimed.
