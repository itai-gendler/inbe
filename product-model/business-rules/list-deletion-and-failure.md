---
appliesTo:
- type: entity
  id: list
- type: entity
  id: todo
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
---

# List deletion includes its Todos in one transaction

Parent-and-child deletion is transactional. Other record writes can precede outbox enqueue failure and do not promise rollback of a committed edit.
