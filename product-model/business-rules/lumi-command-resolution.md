---
appliesTo:
- type: entity
  id: lumi-message
- type: entity
  id: habit
- type: entity
  id: list
- type: entity
  id: todo
- type: entity
  id: diary-entry
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
---

# Lumi resolves bounded references before dispatching actions

Resolve supported names and references within bounded search; ambiguity or no match produces clarification. Recognized app actions retain their own capability and effects.
