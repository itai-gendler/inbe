---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Resume practice — remote sun salutation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  actor: user
- text: A paused local origin or fresh observed paused remote origin is selected; remote control checks matching
    run/revision and absence of a pending request.
  kind: condition
  entities:
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
      place: desktop-app::sun-salutation
  actor: user
- text: A resume request targets fresh observed origin/activity/revision. The observer shows pending control; the
    origin must accept and apply the matching request before progression changes.
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Pending control
    - Control outcome
  contexts:
    desktop:
      place: desktop-app::sun-salutation
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

# Resume practice — remote sun salutation

## Trigger

Resume practice — remote sun salutation.

## Outcome

A resume request targets fresh observed origin/activity/revision. The observer shows pending control; the origin must accept and apply the matching request before progression changes.
