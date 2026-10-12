---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Delete message for the current conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The synthetic greeting has no retained archive identity to remove.
  kind: condition
  entities:
  - entity: lumi-message
    effect: reads
    facts:
    - Archive identity
    - Scope
    - Speaker
    - Text
    - Time
    - Card payload
    - Deletion marker
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The synthetic greeting has no archive identity and cannot be deleted as an archived row.
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

# Delete message — greeting

## Trigger

Delete message for the current conversation.

## Outcome

The synthetic greeting has no archive identity and cannot be deleted as an archived row.
