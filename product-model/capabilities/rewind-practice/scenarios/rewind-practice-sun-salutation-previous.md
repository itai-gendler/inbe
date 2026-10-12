---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Rewind practice — sun salutation previous
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: The supported current Wim Hof round or Sun Salutation movement position determines the previous position;
    Wim Hof first-round rewind resets that round.
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
- text: The previous movement step or repetition boundary becomes current.
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Movement step
    - Repetition progress
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

# Rewind practice — sun salutation previous

## Trigger

Rewind practice — sun salutation previous.

## Outcome

The previous movement step or repetition boundary becomes current.
