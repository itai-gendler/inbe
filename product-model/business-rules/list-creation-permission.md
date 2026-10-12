---
appliesTo:
- type: entity
  id: list
  effect: creates
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform List creation

User saves a named nonblank parent or imports OneList content. Accepted current-context incoming live records create missing parents.
