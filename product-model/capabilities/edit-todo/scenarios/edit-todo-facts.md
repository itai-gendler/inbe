---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Edit todo in the selected List
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
- text: The selected current-scope item and parent exist before its title, comment or order is saved; title trimming
    must retain nonblank content.
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
- text: The addressed todo has its saved edited facts.
  kind: product
  entities:
  - entity: todo
    effect: changes
    facts:
    - Title
    - Comment
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

# Edit todo — facts

## Trigger

Edit todo in the selected List.

## Outcome

The addressed todo has its saved edited facts.
