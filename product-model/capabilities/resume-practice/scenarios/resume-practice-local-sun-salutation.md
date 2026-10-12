---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Resume practice — local sun salutation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: A paused local origin or fresh observed paused remote origin is selected; remote control checks matching
    run/revision and absence of a pending request.
  kind: condition
  entities:
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Movement step
    - Repetition progress
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
  - entity: sun-salutation-settings
    effect: reads
    facts:
    - Repetitions
    - Start timing
    - End timing
    - Character
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: Explicit local resume changes progression at the origin; desktop focus loss does not perform this action.
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Pause
    from: Paused
    to: Running
  contexts:
    desktop:
      place: desktop-app::sun-salutation
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
  target: src/practices/sun_salutation/sun_salutation_session.zi
---

# Resume practice — local sun salutation

## Trigger

Resume practice — local sun salutation.

## Outcome

Explicit local resume changes progression at the origin; desktop focus loss does not perform this action.
