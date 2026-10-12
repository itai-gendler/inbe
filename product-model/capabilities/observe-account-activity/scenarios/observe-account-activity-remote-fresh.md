---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read observed activity or publish the local origin
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: The observed activity has an origin and run identity; publication time and revision distinguish fresh twenty-second
    activity from stale observations.
  kind: condition
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: sync-settings
    effect: reads
    facts:
    - Enabled
    - Exchange status
    - Retry status
    - Pending review
  contexts:
    desktop:
      place: desktop-app
  actor: user
- text: Observed origin/progress within twenty seconds, with at most five seconds future allowance, is fresh and
    can block local start or accept a targeted control request.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app
  actor: user
references:
- kind: code
  role: implementation
  target: src/app/account_activity.zi
- kind: code
  role: implementation
  target: src/app/account_activity_model.zi
- kind: code
  role: implementation
  target: src/app/account_activity_view.zi#ActivityDrawRemote
---

# Observe account activity — remote fresh

## Trigger

Read observed activity or publish the local origin.

## Outcome

Observed origin/progress within twenty seconds, with at most five seconds future allowance, is fresh and can block local start or accept a targeted control request.
