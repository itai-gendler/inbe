---
entities:
- entity: notifications-settings
  shows:
  - Friend requests
  - Habit reminders
  collects:
  - Friend requests
  - Habit reminders
- entity: reminder
  shows:
  - Entry position
  - Practice
  - Enabled
  - Hour
  - Last day
  collects:
  - Practice
  - Enabled
  - Hour
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Notifications

General notification preferences and independently selected reminder entries with practice, enabled state and hour; actual platform delivery is separate.
