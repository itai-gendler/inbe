---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read practice guide — guide sun salutation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: The selected shipped family identifies the guide presented in the same process as its configuration.
  kind: condition
  entities:
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
- text: The Sun Salutation guide is presented in the same practice process as its configuration.
  kind: product
  entities: []
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

# Read practice guide — guide sun salutation

## Trigger

Read practice guide — guide sun salutation.

## Outcome

The Sun Salutation guide is presented in the same practice process as its configuration.
