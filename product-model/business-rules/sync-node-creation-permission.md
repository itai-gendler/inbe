---
appliesTo:
- type: entity
  id: sync-node
  effect: creates
references:
- kind: code
  role: implementation
  target: src/storage/sync_nodes.zi
permits:
- actors:
  - user
---

# User performs Sync node creation

User adds a normalized address within the eight-node list; an existing normalized address resolves its existing entry instead.
