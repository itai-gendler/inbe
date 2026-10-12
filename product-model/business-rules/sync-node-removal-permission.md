---
appliesTo:
- type: entity
  id: sync-node
  effect: removes
references:
- kind: code
  role: implementation
  target: src/storage/sync_nodes.zi
permits:
- actors:
  - user
---

# User performs Sync node removal

User removes a selected node only while at least one usable configured address remains and guarded work is idle.
