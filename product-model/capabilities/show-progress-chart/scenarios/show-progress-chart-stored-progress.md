---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Show progress chart for the current conversation
  kind: actor
  entities:
  - entity: progress-chart
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested stored-progress metric and one-through-thirty-one-day range are resolved before deriving and
    archiving zero-filled dated values.
  kind: condition
  entities:
  - entity: habit-day
    effect: reads
    facts:
    - Habit
    - Date
    - Stored count
    - Stored completion
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Scheduled
    - Completed
  - entity: wim-hof-session
    effect: reads
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Retention values
    - Mood
  - entity: meditation-session
    effect: reads
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Duration
    - Mood
  - entity: patterns-session
    effect: reads
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Recorded duration values
    - Mood
  - entity: sun-salutation-session
    effect: reads
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Repetitions
    - Mood
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: A supported metric over one to thirty-one days uses stored scoped data and zero-filled dates; the archived
    numbers are a snapshot, not invented online values.
  kind: product
  entities:
  - entity: progress-chart
    effect: creates
    facts:
    - Archive identity
    - Scope
    - Message header
    - Metric
    - Date range
    - Dates
    - Snapshot values
    - Deletion marker
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/lumi/lumi.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/cells/lumi_online.zi
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
---

# Show progress chart — stored progress

## Trigger

Show progress chart for the current conversation.

## Outcome

A supported metric over one to thirty-one days uses stored scoped data and zero-filled dates; the archived numbers are a snapshot, not invented online values.
