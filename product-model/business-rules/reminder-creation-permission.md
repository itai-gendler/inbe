---
appliesTo:
- type: entity
  id: reminder
  effect: creates
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
permits:
- actors:
  - user
---

# User performs Reminder creation

User adds an individually selected reminder within sixteen-entry capacity; defaults are enabled Wim Hof at hour eight with last-day zero.
