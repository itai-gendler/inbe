---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Add sync node for the configured node addresses
  kind: actor
  entities:
  - entity: sync-node
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The entered node address is normalized, compared with existing addresses and checked against the eight-node
    capacity.
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
- text: An invalid normalized URL or the eight-node capacity refuses another entry.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
references:
- kind: code
  role: implementation
  target: src/storage/sync_nodes.zi
---

# Add sync node — invalid or capacity

## Trigger

Add sync node for the configured node list.

## Outcome

An invalid normalized URL or the eight-node capacity refuses another entry.
