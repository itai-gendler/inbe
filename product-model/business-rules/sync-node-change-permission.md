---
appliesTo:
- type: entity
  id: sync-node
  effect: changes
references:
- kind: code
  role: implementation
  target: src/storage/sync_nodes.zi
permits:
- actors:
  - user
  when:
  - entity: profile
    fact: Account access mode
    is-not: Delegated
---

# User performs Sync node change

User selects a configured preferred node outside delegated activation restrictions and busy guards. Node activation retains separate cursor, clock and hash state and requests exchange under the actual enabled preference.
