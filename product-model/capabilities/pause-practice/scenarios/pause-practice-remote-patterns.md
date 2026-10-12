---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Pause practice — remote patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: A running local origin or fresh observed remote origin is selected; remote control additionally checks matching
    run/revision and absence of a pending request.
  kind: condition
  entities:
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
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: A pause request targets fresh observed origin/activity/revision. The observer shows pending control; the
    origin must accept and apply the matching request before progression changes.
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Pending control
    - Control outcome
  contexts:
    desktop:
      place: desktop-app::patterns
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

# Pause practice — remote patterns

## Trigger

Pause practice — remote patterns.

## Outcome

A pause request targets fresh observed origin/activity/revision. The observer shows pending control; the origin must accept and apply the matching request before progression changes.
