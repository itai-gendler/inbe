---
kind: primary
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
- text: The selected configured address must exist and the current guarded work must be idle before preferred-node
    activation.
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
- text: The chosen node becomes preferred/active with its node-specific exchange state; existing local queued work
    is retained.
  kind: product
  entities:
  - entity: sync-node
    effect: changes
    facts:
    - Preferred
    - Active
    - Cursor
    - Clock
    - Hash
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
references:
- kind: code
  role: implementation
  target: src/storage/sync_nodes.zi
---

# Choose sync node — preferred

## Trigger

Choose sync node for the configured node list.

## Outcome

The chosen node becomes preferred/active with its node-specific exchange state; existing local queued work is retained.
