---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Resume practice — local wim hof
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: A paused local origin or fresh observed paused remote origin is selected; remote control checks matching
    run/revision and absence of a pending request.
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
- text: Explicit local resume changes progression at the origin; desktop focus loss does not perform this action.
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: changes
    facts:
    - Pause
    from: Paused
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

# Resume practice — local wim hof

## Trigger

Resume practice — local wim hof.

## Outcome

Explicit local resume changes progression at the origin; desktop focus loss does not perform this action.
