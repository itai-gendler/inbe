---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Exit practice — discard wim hof
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: The unfinished originating process and its pause and elapsed/completed progress determine whether discard,
    qualifying partial save or cancellation is offered.
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
- text: Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit;
    no normal completion summary is produced.
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

# Exit practice — discard wim hof

## Trigger

Exit practice — discard wim hof.

## Outcome

Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit; no normal completion summary is produced.
