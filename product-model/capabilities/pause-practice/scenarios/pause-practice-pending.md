---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Pause practice — pending
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: The selected observed run already has a pending control request
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
    - Pending control
    - Control outcome
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
    - Pending control
    - Control outcome
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
    - Pending control
    - Control outcome
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Pause
    - Pending control
    - Control outcome
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: Refuse another control request without changing origin progress or replacing pending work
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
references:
- kind: code
  role: implementation
  target: src/app/account_activity.zi#ActivityRequestPause
- kind: code
  role: implementation
  target: src/app/account_activity_model.zi#ActivityControlMatches
- kind: code
  role: implementation
  target: src/app/account_activity_view.zi#ActivityDrawRemote
---

# Pause practice — pending

## Trigger

Pause practice — pending.

## Outcome

An already pending control disables another request until acknowledgement or expiry.
