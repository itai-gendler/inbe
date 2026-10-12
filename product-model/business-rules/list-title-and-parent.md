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

# List and Todo titles require valid current-scope records

Trim and refuse blank titles. Todo creation resolves an existing addressed parent in the current record scope.
