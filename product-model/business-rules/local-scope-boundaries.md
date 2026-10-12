---
appliesTo:
- type: entity
  id: habit
- type: entity
  id: habit-day
- type: entity
  id: list
- type: entity
  id: todo
- type: entity
  id: diary-entry
- type: entity
  id: lumi-message
- type: entity
  id: progress-chart
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
---

# Retained data uses each implemented scope predicate

Session loader, materializer, chart and cell archive queries have differing scope predicates. They do not imply a universal User ownership relation or identical local-file/account-record boundaries.
