---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to reopen the referenced item
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The addressed current-scope item is complete before reopening saves it as incomplete.
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
- text: The addressed todo is incomplete again.
  kind: product
  entities:
  - entity: todo
    effect: changes
    facts:
    - Completion
    from: Complete
    to: Incomplete
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

# Reopen todo — lumi

## Trigger

Reopen todo in the selected List.

## Outcome

The addressed todo is incomplete again.
