---
appliesTo:
- type: entity
  id: sun-salutation-session
  effect: changes
references:
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Sun Salutation session change

User saves optional mood or maintains this family’s exposed recorded values where an editor exists. Incoming accepted records use timestamp/pending-edit predicates; Meditation and Sun Salutation do not gain the other families’ value editor.
