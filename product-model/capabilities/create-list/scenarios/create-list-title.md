---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Create list in the selected List
  kind: actor
  entities:
  - entity: list
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: The entered parent title is trimmed and must remain nonblank before a new addressed parent is saved.
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
- text: A trimmed named list is saved in the current data context; Item creation requires the addressed parent.
  kind: product
  entities:
  - entity: list
    effect: creates
    facts:
    - Identity
    - Scope
    - Title
    - Order
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

# Create list — title

## Trigger

Create list in the selected List.

## Outcome

A trimmed named list is saved in the current data context; Todo creation requires the addressed parent.
