---
kind: primary
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
- text: The selected configured address exists, at least one other address remains and guarded exchange work is
    idle before removal.
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
- text: The selected nonfinal node is removed and a usable node addresses remains.
  kind: product
  entities:
  - entity: sync-node
    effect: removes
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
references:
- kind: code
  role: implementation
  target: src/storage/sync_nodes.zi
---

# Remove sync node — node

## Trigger

Remove sync node for the configured node list.

## Outcome

The selected nonfinal node is removed and a usable node list remains.
