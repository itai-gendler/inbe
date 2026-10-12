---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Exit practice — cancelled
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: The unfinished run has an exit confirmation open and User chooses Cancel rather than save or discard.
  kind: condition
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Pause
    - Result values
    - Save outcome
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Pause
    - Result values
    - Save outcome
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Pause
    - Result values
    - Save outcome
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Pause
    - Result values
    - Save outcome
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: Close only the exit confirmation; retain the selected live run and its existing pause/progress without save
    or discard
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
references:
- kind: code
  role: implementation
  target: src/app/application.zi
---

# Exit practice — cancelled

## Trigger

Exit practice — cancelled.

## Outcome

Cancel closes the exit confirmation and retains the active process without saving or discarding.

## Edge cases

- The same outcome applies to Wim Hof, Meditation, Breathing Patterns, Sun Salutation through their exposed live exit confirmations.
