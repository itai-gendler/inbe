---
appliesTo:
- type: entity
  id: reminder
  effect: removes
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
permits:
- actors:
  - user
---

# User performs Reminder removal

User removes a selected reminder and persists the remaining entry positions.
