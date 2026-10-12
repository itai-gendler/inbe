---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Exit practice — discard sun salutation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: The unfinished originating process and its pause and elapsed/completed progress determine whether discard,
    qualifying partial save or cancellation is offered.
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
- text: Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit;
    no normal completion summary is produced.
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: removes
    from: Running
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

# Exit practice — discard sun salutation

## Trigger

Exit practice — discard sun salutation.

## Outcome

Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit; no normal completion summary is produced.
