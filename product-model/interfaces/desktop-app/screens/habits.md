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
  collects:
  - Stored count
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_linked_rules.zi
---

# Habits

Habit definitions and date progress, including schedule, target, stored-linked effective count and completion.
