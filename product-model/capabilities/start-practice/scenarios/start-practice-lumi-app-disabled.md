---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Start practice — lumi app disabled
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested practice app is disabled or its package is unavailable before the Lumi start action can run.
  kind: condition
  entities:
  - entity: apps-settings
    effect: reads
    facts:
    - Lumi installed
    - Practices available
  - entity: profile
    effect: reads
    facts:
    - Account access mode
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The Lumi start does not run while the target practice app is disabled or unavailable.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
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
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Start practice — lumi app disabled

## Trigger

Start practice — lumi app disabled.

## Outcome

The Lumi start does not run while the target practice app is disabled or unavailable.
