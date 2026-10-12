---
appliesTo:
- type: entity
  id: notifications-settings
  effect: changes
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
permits:
- actors:
  - user
---

# User performs Notifications settings change

User saves the general friend-request and Habit-reminder preferences. Independently addressed reminder entries use their own operations; actual scheduling and delivery are separate.
