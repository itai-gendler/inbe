---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Browse lists in the selected List
  kind: actor
  entities:
  - entity: list
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: The selected existing parent and completion filter determine which current-scope items are presented.
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
- text: Current-scope Lists and Todos are shown with selection and completion filtering.
  kind: product
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

# Browse lists — lists and todos

## Trigger

Browse lists in the selected List.

## Outcome

Current-scope Lists and Todos are shown with selection and completion filtering.
