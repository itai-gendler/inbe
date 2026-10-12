---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Delete list in the selected List
  kind: actor
  entities:
  - entity: list
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: The addressed parent and its complete and incomplete children are identified for one transactional removal.
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
- text: Cancellation retains the List and its children.
  kind: product
  entities:
  - entity: list
    effect: reads
    facts: []
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

# Delete list — cancelled

## Trigger

Delete list in the selected List.

## Outcome

Cancellation retains the List and its children.
