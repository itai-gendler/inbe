---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Start practice — fresh remote
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: A fresh active remote account observation exists within the twenty-second window, so a new local originating
    process is not started.
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
- text: Fresh observed account activity prevents a new local start; this does not provide a distributed lock for
    simultaneous offline starts.
  kind: product
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
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

# Start practice — fresh remote

## Trigger

Start practice — fresh remote.

## Outcome

Fresh observed account activity prevents a new local start; this does not provide a distributed lock for simultaneous offline starts.
