---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Discard practice result — result delete failed
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: An ordinary saved result is selected for discard, but its retained-record deletion fails before result closure.
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
- text: When the ordinary result belongs to Wim Hof, retain that result and expose its write failure
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: changes
    facts:
    - Save outcome
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: When the ordinary result belongs to Meditation, retain that result and expose its write failure
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Save outcome
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: When the ordinary result belongs to Breathing Patterns, retain that result and expose its write failure
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Save outcome
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: When the ordinary result belongs to Sun Salutation, retain that result and expose its write failure
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Save outcome
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
references:
- kind: code
  role: implementation
  target: src/practices/session_results.zi
---

# Discard practice result — result delete failed

## Trigger

Discard practice result — result delete failed.

## Outcome

A failed deletion retains the ordinary result and displays its write failure; the saved record is not claimed removed.

## Decision points

### Result family

Which ordinary result encountered the failure?

- Wim Hof → retain the ordinary result, expose the failure and keep the saved record.
- Meditation → retain the ordinary result, expose the failure and keep the saved record.
- Breathing Patterns → retain the ordinary result, expose the failure and keep the saved record.
- Sun Salutation → retain the ordinary result, expose the failure and keep the saved record.
