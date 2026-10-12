---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Change practice settings — configuration sun salutation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: The selected family loads its saved configuration before the requested practice parameters are persisted.
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
- text: The Sun Salutation settings persist for subsequent use; the family keeps its own configuration facts.
  kind: product
  entities:
  - entity: sun-salutation-settings
    effect: changes
    facts:
    - Repetitions
    - Start timing
    - End timing
    - Character
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

# Change practice settings — configuration sun salutation

## Trigger

Change practice settings — configuration sun salutation.

## Outcome

The Sun Salutation settings persist for subsequent use; the family keeps its own configuration facts.
