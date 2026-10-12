---
appliesTo:
- type: entity
  id: sun-salutation-session
  effect: removes
references:
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Sun Salutation session removal

User removes an addressed saved result or its last exposed positive value where supported. Scoped clearing and accepted incoming deletion markers remove it from active history; synchronization tombstones can remain.
