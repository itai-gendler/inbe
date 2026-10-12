---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Start practice — lumi sun salutation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested family, existing local process and fresh remote activity determine new start, same-process
    restoration or refusal; saved configuration supplies the new run.
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
      place: desktop-app::lumi
  actor: user
- text: A new originating Sun Salutation process starts from its saved settings. Lumi origin is retained and the
    Product carries User into this practice.
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: creates
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
    to: Running
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Carry User into the newly started process
  kind: product
  actor: user
  entities: []
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
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Start practice — lumi sun salutation

## Trigger

Start practice — lumi sun salutation.

## Outcome

A new originating Sun Salutation process starts from its saved settings. Lumi origin is retained and the Product carries User into this practice.
