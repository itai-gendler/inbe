---
appliesTo:
- type: entity
  id: reminder
  effect: changes
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
permits:
- actors:
  - user
---

# User performs Reminder change

User saves a valid selected entry’s enabled state, one of four practices and hour zero through twenty-three.
