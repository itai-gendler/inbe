---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: The selected outstanding remote-control request reaches its twenty-second expiry without a matching acknowledgement
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
  unattended: true
- text: When the pending request concerns Wim Hof, clear its pending display without asserting origin application
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: changes
    facts:
    - Pending control
    - Control outcome
  contexts:
    desktop:
      place: desktop-app
- text: When the pending request concerns Meditation, clear its pending display without asserting origin application
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Pending control
    - Control outcome
  contexts:
    desktop:
      place: desktop-app
- text: When the pending request concerns Breathing Patterns, clear its pending display without asserting origin
    application
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Pending control
    - Control outcome
  contexts:
    desktop:
      place: desktop-app
- text: When the pending request concerns Sun Salutation, clear its pending display without asserting origin application
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Pending control
    - Control outcome
  contexts:
    desktop:
      place: desktop-app
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

# Pause practice — expiry

## Trigger

Pause practice — expiry.

## Outcome

After the control expiry window, pending display clears without claiming that the origin applied the request.

## Decision points

### Observed family

Which observed run held the expired request?

- Wim Hof → clear only that run’s pending display; do not claim origin application.
- Meditation → clear only that run’s pending display; do not claim origin application.
- Breathing Patterns → clear only that run’s pending display; do not claim origin application.
- Sun Salutation → clear only that run’s pending display; do not claim origin application.
