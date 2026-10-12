---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Import data with the native data controls
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::data
  actor: user
- text: The selected supported archive, database, Tickmate or bounded OneList input determines record deduplication,
    definition/count merging and optional whitelisted preference restoration.
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
    as: matched-definition
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
    as: matched-date
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
- text: Positive canonical sessions are deduplicated, check-ins are added when new, Habit definitions merge by implemented
    identity/name handling and day counts use import maximum handling. Description, schedule and reminder fields
    are not universally restored.
  kind: product
  entities:
  - entity: habit
    effect: changes
    facts:
    - Color
    - Order
    - Practice links
    - Linking mode
    - Counting mode
    - Target
    as: matched-definition
  - entity: habit-day
    effect: changes
    facts:
    - Stored count
    - Stored completion
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Completed
    as: matched-date
  - entity: reminder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::data
  actor: user
- text: Insert positive canonical records absent locally; duplicate records retain their existing local check-ins
  kind: product
  actor: user
  entities:
  - entity: wim-hof-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Retention values
    - Mood
  - entity: meditation-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Duration
    - Mood
  - entity: patterns-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Recorded duration values
    - Mood
  - entity: sun-salutation-session
    effect: creates
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
- text: Import a new unmatched definition and its previously absent day while retaining defaults for unimported
    fields
  kind: product
  actor: user
  entities:
  - entity: habit
    effect: creates
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
    as: new-definition
  - entity: habit-day
    effect: creates
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
    as: new-date
    with: new-definition
  contexts:
    desktop:
      place: desktop-app::data
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

# Import data — data

## Trigger

Import data with the native data controls.

## Outcome

Positive canonical sessions are deduplicated, check-ins are added when new, Habit definitions merge by implemented identity/name handling and day counts use import maximum handling. Description, schedule and reminder fields are not universally restored.

## Edge cases

- Duplicate canonical sessions do not overwrite existing local check-ins; only a newly inserted session imports its check-in.
- These SQLite paths do not restore Lists/Todos or every retained field merely because a ZIP snapshot contains them.
