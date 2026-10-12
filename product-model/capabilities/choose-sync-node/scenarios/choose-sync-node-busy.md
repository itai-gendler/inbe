---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Choose sync node for the configured node addresses
  kind: actor
  entities:
  - entity: sync-node
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Guarded exchange work is busy, so preferred-node activation is deferred.
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
- text: Busy guarded work prevents selecting another active/preferred node.
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

# Choose sync node — busy

## Trigger

Choose sync node for the configured node list.

## Outcome

Busy guarded work prevents selecting another active/preferred node.
