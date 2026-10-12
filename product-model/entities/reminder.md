---
domain: notifications
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Reminder

An individually addressed local reminder entry.

## Information kept

- **Entry position** — Individually selected position in the saved local reminder entries.
- **Practice** — One of the four shipped practices selected for this reminder.
- **Enabled** — Whether this reminder entry is enabled.
- **Hour** — Selected local hour from zero through twenty-three.
- **Last day** — Last-day bookkeeping retained for scheduling; a new reminder initializes it to zero.
