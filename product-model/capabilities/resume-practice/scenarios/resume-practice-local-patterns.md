---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Resume practice — local patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: A paused local origin or fresh observed paused remote origin is selected; remote control checks matching
    run/revision and absence of a pending request.
  kind: condition
  entities:
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Ratio
    - Phase
    - Cycle
    - Duration
    - Elapsed progress
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
  - entity: patterns-settings
    effect: reads
    facts:
    - Preset
    - Phase durations
    - Session duration
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: Explicit local resume changes progression at the origin; desktop focus loss does not perform this action.
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Pause
    from: Paused
    to: Running
  contexts:
    desktop:
      place: desktop-app::patterns
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
  target: src/practices/patterns/patterns_practice.zi
---

# Resume practice — local patterns

## Trigger

Resume practice — local patterns.

## Outcome

Explicit local resume changes progression at the origin; desktop focus loss does not perform this action.
