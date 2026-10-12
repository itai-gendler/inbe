---
appliesTo:
- type: entity
  id: list
  effect: removes
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform List removal

User confirms transactional parent-and-child deletion or selects SQL replacement. Accepted deletion markers exclude parents from active history without claiming rollback of unrelated earlier writes.
