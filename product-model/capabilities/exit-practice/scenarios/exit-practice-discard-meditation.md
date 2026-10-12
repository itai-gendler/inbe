---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Exit practice — discard meditation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: The unfinished originating process and its pause and elapsed/completed progress determine whether discard,
    qualifying partial save or cancellation is offered.
  kind: condition
  entities:
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Duration
    - Remaining time
    - Elapsed progress
    - Extension state
    - Waiting state
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
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
- text: Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit;
    no normal completion summary is produced.
  kind: product
  entities:
  - entity: meditation-practice
    effect: removes
    from: Running
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

# Exit practice — discard meditation

## Trigger

Exit practice — discard meditation.

## Outcome

Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit; no normal completion summary is produced.
