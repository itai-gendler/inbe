---
entities:
- entity: habit
  shows:
  - Identity
  - Name
  - Description
  - Color
  - Order
  - Practice links
  - Linking mode
  - Counting mode
  - Target
  - Schedule
  - Reminder hour
  collects:
  - Name
  - Description
  - Color
  - Practice links
  - Counting mode
  - Target
  - Schedule
  - Reminder hour
- entity: habit-day
  shows:
  - Habit
  - Date
  - Stored count
  - Stored completion
  - Materialized baseline
  - Visible linked count
  - Effective count
  - Scheduled
  - Completed
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_linked_rules.zi
---

# Habit

One selected definition, its descriptive and linking preferences, calendar and derived statistics.
