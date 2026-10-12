---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi about the selected custom appearance
  kind: actor
  entities:
  - entity: custom-appearance
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: The current scope is prefixed into the composer and the Product opens Lumi. The prompt is not automatically
    submitted.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/lumi/lumi.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/cells/lumi_online.zi
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
---

# Send message — appearance help

## Trigger

Ask Lumi about the selected custom appearance.

## Outcome

The current scope is prefixed into the composer and the Product opens Lumi. The prompt is not automatically submitted.
