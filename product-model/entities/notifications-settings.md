---
domain: notifications
relations:
- entity: reminder
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Notifications settings

General notification preferences.

## Information kept

- **Friend requests** — Preference for friend-request notifications.
- **Habit reminders** — General preference for Habit reminders; it does not prove platform delivery.
