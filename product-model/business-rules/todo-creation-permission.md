---
appliesTo:
- type: entity
  id: todo
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

# User and applicable Product processing perform Todo creation

User adds a nonblank item to an existing current-scope parent or imports supported content. Accepted incoming items retain their actual incomplete or complete state; a new parent can precede its items.
