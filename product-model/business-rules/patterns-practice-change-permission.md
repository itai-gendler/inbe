---
appliesTo:
- type: entity
  id: patterns-practice
  effect: changes
references:
- kind: code
  role: implementation
  target: src/practices/patterns/patterns_practice.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Breathing Patterns practice change

User controls the local origin or requests control of a fresh observed run. Originating timer progression and matching control application update only that run; observers never advance origin time or save a duplicate result.
