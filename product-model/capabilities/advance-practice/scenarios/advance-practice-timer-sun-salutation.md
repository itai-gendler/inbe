---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: The originating live timer reaches the next breath, phase, movement or duration boundary
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
  unattended: true
- text: Movement steps and repetitions advance through their timing.
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

# Advance practice — timer sun salutation

## Trigger

Advance practice — timer sun salutation.

## Outcome

Movement steps and repetitions advance through their timing.
