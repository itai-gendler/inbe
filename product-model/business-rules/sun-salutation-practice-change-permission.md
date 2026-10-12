---
appliesTo:
- type: entity
  id: sun-salutation-practice
  effect: changes
references:
- kind: code
  role: implementation
  target: src/practices/sun_salutation/sun_salutation_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Sun Salutation practice change

User controls the local origin or requests control of a fresh observed run. Originating timer progression and matching control application update only that run; observers never advance origin time or save a duplicate result.
