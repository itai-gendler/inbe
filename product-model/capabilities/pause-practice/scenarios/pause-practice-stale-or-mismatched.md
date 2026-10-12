---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Pause practice — stale or mismatched
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: The selected observed origin, run identity, revision or publication freshness fails the control match
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

# Pause practice — stale or mismatched

## Trigger

Pause practice — stale or mismatched.

## Outcome

A stale or mismatched origin/activity/revision is refused without changing origin progression.
