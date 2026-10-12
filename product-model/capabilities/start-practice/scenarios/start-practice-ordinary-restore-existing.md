---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Start practice — ordinary restore existing
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::practices
  actor: user
- text: The requested family, existing local process and fresh remote activity determine new start, same-process
    restoration or refusal; saved configuration supplies the new run.
  kind: condition
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
  - entity: apps-settings
    effect: reads
    facts:
    - Practices available
  - entity: account
    effect: reads
    facts:
    - Identity
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: When the matching active run is Wim Hof, carry User to that existing process without starting or saving
    a duplicate
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Pause
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: When the matching active run is Meditation, carry User to that existing process without starting or saving
    a duplicate
  kind: product
  entities:
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Pause
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: When the matching active run is Breathing Patterns, carry User to that existing process without starting
    or saving a duplicate
  kind: product
  entities:
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Pause
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: When the matching active run is Sun Salutation, carry User to that existing process without starting or
    saving a duplicate
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
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
  target: src/practices/whm/whm_session.zi
---

# Start practice — ordinary restore existing

## Trigger

Start practice — ordinary restore existing.

## Outcome

The existing local process is restored without creating a duplicate. Ordinary restore uses the active process; Lumi restoration requires the requested same kind.

## Decision points

### Existing family

Which live run is restored?

- Wim Hof → restore its live process without a duplicate creation.
- Meditation → restore its live process without a duplicate creation.
- Breathing Patterns → restore its live process without a duplicate creation.
- Sun Salutation → restore its live process without a duplicate creation.
