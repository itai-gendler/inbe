---
appliesTo:
- type: entity
  id: todo
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

# User and applicable Product processing perform Todo change

User edits title/comment/order, completes or reopens an item. Accepted incoming records preserve the implemented conflict handling, and enqueue failure after a record write does not promise rollback.
