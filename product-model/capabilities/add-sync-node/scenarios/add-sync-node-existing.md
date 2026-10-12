---
kind: primary
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
- text: A duplicate normalized address resolves the existing entry rather than creating another node.
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

# Add sync node — existing

## Trigger

Add sync node for the configured node list.

## Outcome

A duplicate normalized address resolves the existing entry rather than creating another node.
