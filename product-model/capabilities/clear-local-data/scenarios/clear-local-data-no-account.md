---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Clear local data with the native data controls
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::data
  actor: user
- text: Available local credentials select physical deletion or queued tombstones for saved practice and Habit
    data; unrelated cell records and preferences remain.
  kind: condition
  entities:
  - entity: profile
    effect: reads
    facts:
    - Local data context
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
- text: The implemented practice/Habit/day scope is physically deleted without a local account. Other app records
    and general preferences remain outside this clearing scope.
  kind: product
  entities:
  - entity: habit
    effect: removes
  - entity: habit-day
    effect: removes
    with: habit
  - entity: wim-hof-session
    effect: removes
  - entity: meditation-session
    effect: removes
  - entity: patterns-session
    effect: removes
  - entity: sun-salutation-session
    effect: removes
  - entity: account
    effect: reads
    facts: []
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
- kind: code
  role: implementation
  target: src/storage/data.zi#data_delete_all
---

# Clear local data — no account

## Trigger

Clear local data with the native data controls.

## Outcome

The implemented practice/Habit/day scope is physically deleted without a local account. Lists, Diary, Lumi and general preferences remain outside this clearing scope.
