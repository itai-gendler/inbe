---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Create todo in the selected List
  kind: actor
  entities:
  - entity: todo
    effect: reads
    facts: []
  - entity: list
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: A nonblank entered title and an existing selected current-scope parent are required before the new item
    is saved.
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
      place: desktop-app::lists
  actor: user
- text: A trimmed named todo is saved in the current data context; Item creation requires the addressed parent.
  kind: product
  entities:
  - entity: todo
    effect: creates
    facts:
    - Identity
    - Scope
    - Parent List
    - Title
    - Comment
    - Order
    - Completion
    to: Incomplete
  contexts:
    desktop:
      place: desktop-app::lists
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
---

# Create todo — lists

## Trigger

Create todo in the selected List.

## Outcome

A trimmed named todo is saved in the current data context; Todo creation requires the addressed parent.
