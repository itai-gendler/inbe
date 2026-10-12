---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Delete todo in the selected List
  kind: actor
  entities:
  - entity: todo
    effect: reads
    facts: []
    as: addressed-items
  - entity: list
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: The selected existing item is identified in its parent; both incomplete and complete items use the
    removal operation.
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
- text: If the addressed item is incomplete, remove that item from active records
  kind: product
  entities:
  - entity: todo
    effect: removes
    from: Incomplete
    as: incomplete-items
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: If the alternative addressed item is complete, remove that item from active records
  kind: product
  entities:
  - entity: todo
    effect: removes
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

# Delete todo — todo

## Trigger

Delete todo in the selected List.

## Outcome

The addressed todo leaves active records.

## Edge cases

- A selected completed item is removed by the same deletion operation as an incomplete item.

## Decision points

### Addressed completion

Which selected item is removed?

- Incomplete → remove the selected incomplete item.
- Complete → remove the selected completed item through the same operation.
