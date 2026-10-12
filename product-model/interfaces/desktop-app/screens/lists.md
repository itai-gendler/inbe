---
entities:
- entity: list
  shows:
  - Identity
  - Scope
  - Title
  - Order
  collects:
  - Title
- entity: todo
  shows:
  - Identity
  - Scope
  - Parent List
  - Title
  - Comment
  - Order
  - Completion
  collects:
  - Title
  - Comment
  - Completion
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
---

# Lists

The selected named List and its Todos, including comments, order, completion and filtering, with inline creation and maintenance.
