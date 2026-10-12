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
- entity: wim-hof-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Retention values
  - Mood
  collects:
  - Retention values
- entity: meditation-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Duration
  - Mood
- entity: patterns-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Recorded duration values
  - Mood
  collects:
  - Recorded duration values
- entity: sun-salutation-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Repetitions
  - Mood
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_linked_rules.zi
---

# Habit Day

One selected date of a definition, with stored and linked progress and matching saved-session history and maintenance.
