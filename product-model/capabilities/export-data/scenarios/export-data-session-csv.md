---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Export data with the native data controls
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::data
  actor: user
- text: The selected database ZIP or session CSV export determines snapshot or undeleted-record reads and the Linux
    file publication path.
  kind: condition
  entities:
  - entity: profile
    effect: reads
    facts:
    - Local data context
    - Display name
    - Intention
    - Picture
    - Setup progress
    - Local counts
    - Account access mode
  - entity: account
    effect: reads
    facts:
    - Identity
    - Alias
    - Proposed identity
    - Installed identity
  - entity: habit
    effect: reads
    facts:
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
  - entity: list
    effect: reads
    facts:
    - Identity
    - Scope
    - Title
    - Order
  - entity: todo
    effect: reads
    facts:
    - Identity
    - Scope
    - Parent List
    - Title
    - Comment
    - Order
    - Completion
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
      place: desktop-app::data
  actor: user
- text: Undeleted saved sessions export date, activity, source and summed recorded duration through the Linux file
    path.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::data
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_data_ui.zi
- kind: code
  role: implementation
  target: src/storage/import.zi
- kind: code
  role: implementation
  target: src/storage/export_sql.zi
- kind: code
  role: implementation
  target: src/storage/archive_file_linux.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Export data — session csv

## Trigger

Export data with the native data controls.

## Outcome

Undeleted saved sessions export date, activity, source and summed recorded duration through the Linux file path.
