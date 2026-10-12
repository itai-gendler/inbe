---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Pause practice — local meditation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: A running local origin or fresh observed remote origin is selected; remote control additionally checks matching
    run/revision and absence of a pending request.
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
- text: Explicit local pause changes progression at the origin; desktop focus loss does not perform this action.
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Pause
    from: Running
    to: Paused
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

# Pause practice — local meditation

## Trigger

Pause practice — local meditation.

## Outcome

Explicit local pause changes progression at the origin; desktop focus loss does not perform this action.
