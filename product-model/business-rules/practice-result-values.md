---
appliesTo:
- type: entity
  id: wim-hof-session
- type: entity
  id: meditation-session
- type: entity
  id: patterns-session
- type: entity
  id: sun-salutation-session
references:
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Practice-origin saves contain qualifying recorded progress

Wim Hof saves positive completed retention values once. Meditation and Patterns partial saves require at least sixty elapsed seconds. Sun Salutation saves positive repetitions and does not offer the same partial-save exit. Imports follow their own record predicates.
