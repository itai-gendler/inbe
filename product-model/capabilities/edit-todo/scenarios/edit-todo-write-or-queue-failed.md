---
kind: edge
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
- text: The selected current-scope item and parent exist before its title, comment or order is saved; title
    trimming must retain nonblank content.
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
- text: If the scoped SQL update fails or finds no live item, report failure without claiming a committed edit
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
- text: If the SQL update commits but enqueue fails, report failure while retaining the written title, comment
    and order; no full rollback is promised
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

# Edit todo — write or queue failed

## Trigger

Edit todo in the selected List.

## Outcome

A failed write or outbox enqueue is reported; enqueue failure may follow a committed record write and does not promise rollback.

## Decision points

### Failed persistence stage

Which operation failed?

- SQL update → no committed edit is claimed.
- Outbox enqueue after the update → retain the committed item edit despite the failure return.
