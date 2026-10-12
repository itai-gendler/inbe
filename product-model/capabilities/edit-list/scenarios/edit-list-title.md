---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Edit list in the selected List
  kind: actor
  entities:
  - entity: list
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: The selected current-scope parent exists and its entered replacement title remains nonblank after trimming.
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
- text: The addressed list has its saved edited facts.
  kind: product
  entities:
  - entity: list
    effect: changes
    facts:
    - Title
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

# Edit list — title

## Trigger

Edit list in the selected List.

## Outcome

The addressed list has its saved edited facts.
