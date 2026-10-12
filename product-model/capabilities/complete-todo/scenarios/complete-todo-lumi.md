---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to complete the referenced item
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The addressed item exists in the selected current-scope parent and is incomplete before completion is saved.
  kind: condition
  entities:
  - entity: list
    effect: reads
    facts:
    - Identity
    - Scope
    - Title
    - Order
  - entity: todo
    effect: reads
    facts:
    - Identity
    - Scope
    - Parent List
    - Title
    - Comment
    - Order
    - Completion
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The addressed todo is complete.
  kind: product
  entities:
  - entity: todo
    effect: changes
    facts:
    - Completion
    from: Incomplete
    to: Complete
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/lists/lists.zi
- kind: code
  role: implementation
  target: src/screens/elist_screen.zi
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Complete todo — lumi

## Trigger

Complete todo in the selected List.

## Outcome

The addressed todo is complete.
