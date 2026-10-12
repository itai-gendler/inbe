---
appliesTo:
- type: entity
  id: list
  effect: changes
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform List change

User saves the parent title or order. Accepted incoming records update existing parent facts under their conflict predicates.
