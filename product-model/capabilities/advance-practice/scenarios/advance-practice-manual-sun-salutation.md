---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Advance practice — manual sun salutation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: The originating live process is running at a supported manual progression point; the selected phase or movement
    position determines the next step.
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
- text: Explicit next advances the movement step and repetition boundary.
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Movement step
    - Repetition progress
    - Pause
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

# Advance practice — manual sun salutation

## Trigger

Advance practice — manual sun salutation.

## Outcome

Explicit next advances the movement step and repetition boundary.
