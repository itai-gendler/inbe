---
domain: habits
relations:
- entity: habit-day
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_linked_rules.zi
---

# Habit

An independently addressed Habit definition.

## Information kept

- **Identity** — Address distinguishing this definition during local edits and exchange.
- **Name** — Trimmed nonblank displayed name, unique within the loaded native definition set.
- **Description** — Locally saved descriptive text omitted from the mapped Habit exchange fields.
- **Color** — Saved color assigned to this Habit.
- **Order** — Saved position among Habit definitions.
- **Practice links** — Selected practice families whose matching dated saved sessions contribute linked progress.
- **Linking mode** — Saved linking choice interpreted with practice links; it is not an account synchronization opt-out.
- **Counting mode** — Whether day progress uses the counter and target rather than ordinary manual completion.
- **Target** — Configured counter goal, interpreted with a minimum target of one.
- **Schedule** — Selected weekdays; an empty weekday selection means daily.
- **Reminder hour** — Saved hour preference for this Habit reminder; actual delivery is a separate unmapped contract.
