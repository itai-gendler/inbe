---
kind: primary
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
- text: The addressed parent and its complete and incomplete children are identified for one transactional
    removal.
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
    as: addressed-items
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: The addressed list leaves active records. Its children leave in the same transaction.
  kind: product
  entities:
  - entity: list
    effect: removes
  - entity: todo
    effect: removes
    with: list
    from: Incomplete
    as: incomplete-items
  - entity: todo
    effect: removes
    with: list
    from: Complete
    as: complete-items
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

# Delete list — list and todos

## Trigger

Delete list in the selected List.

## Outcome

The addressed list leaves active records. Its children leave in the same transaction.

## Edge cases

- Parent deletion includes completed and incomplete children in the same transaction.
