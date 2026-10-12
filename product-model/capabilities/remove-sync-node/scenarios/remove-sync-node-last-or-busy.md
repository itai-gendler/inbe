---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Remove sync node for the configured node addresses
  kind: actor
  entities:
  - entity: sync-node
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The selected node is the final configured address or guarded exchange work is busy, so removal is refused.
  kind: condition
  entities:
  - entity: sync-node
    effect: reads
    facts:
    - Scope
    - Address
    - Order
    - Preferred
    - Active
    - Cursor
    - Clock
    - Hash
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Removing the final configured address or changing the list while guarded work is busy is refused.
  kind: product
  entities:
  - entity: list
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
references:
- kind: code
  role: implementation
  target: src/storage/sync_nodes.zi
---

# Remove sync node — last or busy

## Trigger

Remove sync node for the configured node list.

## Outcome

Removing the last node or changing the list while guarded work is busy is refused.
