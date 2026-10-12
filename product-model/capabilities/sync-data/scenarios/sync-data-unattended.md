---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Enabled current-account synchronization reaches a scheduled attempt or pending local exchange work
  kind: condition
  entities:
  - entity: sync-settings
    effect: reads
    facts:
    - Enabled
    - Exchange status
    - Retry status
    - Pending review
  - entity: account
    effect: reads
    facts:
    - Identity
    - Private key
    - Alias
    - Proposed identity
    - Installed identity
  contexts:
    desktop:
      place: desktop-app
  unattended: true
- text: For incoming records that already exist and pass the actual timestamp and pending-local-edit checks,
    apply their changed progress and definition facts; preserve local descriptive text omitted from the wire
  kind: product
  entities:
  - entity: habit
    effect: changes
    facts:
    - Name
    - Color
    - Order
    - Practice links
    - Linking mode
    - Counting mode
    - Target
    - Schedule
    - Reminder hour
    as: existing-habit
  - entity: habit-day
    effect: changes
    facts:
    - Stored count
    - Stored completion
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Completed
    as: existing-habit-day
  - entity: list
    effect: changes
    facts:
    - Title
    - Order
    as: existing-list
  - entity: todo
    effect: changes
    facts:
    - Title
    - Comment
    - Order
    - Completion
    as: existing-todo
  - entity: wim-hof-session
    effect: changes
    facts:
    - Local date
    - Local time
    - Source
    - Retention values
    - Mood
    as: existing-wim-hof-session
  - entity: meditation-session
    effect: changes
    facts:
    - Local date
    - Local time
    - Source
    - Duration
    - Mood
    as: existing-meditation-session
  - entity: patterns-session
    effect: changes
    facts:
    - Local date
    - Local time
    - Source
    - Recorded duration values
    - Mood
    as: existing-patterns-session
  - entity: sun-salutation-session
    effect: changes
    facts:
    - Local date
    - Local time
    - Source
    - Repetitions
    - Mood
    as: existing-sun-salutation-session
  contexts:
    desktop:
      place: desktop-app::account
- text: When the accepted live habit record is absent locally, create its retained facts with defaults for
    unexchanged fields
  kind: product
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
    as: new-habit
  contexts:
    desktop:
      place: desktop-app::account
- text: When the accepted live habit day record is absent locally, create its retained facts with defaults
    for unexchanged fields
  kind: product
  entities:
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
    as: new-habit-day
  contexts:
    desktop:
      place: desktop-app::account
- text: When the accepted live list record is absent locally, create its retained facts with defaults for unexchanged
    fields
  kind: product
  entities:
  - entity: list
    effect: creates
    facts:
    - Identity
    - Scope
    - Title
    - Order
    as: new-list
  contexts:
    desktop:
      place: desktop-app::account
- text: When the absent incoming item belongs to an existing or newly created parent and its completion is
    incomplete, create it in that state
  kind: product
  entities:
  - entity: todo
    effect: creates
    to: Incomplete
    facts:
    - Identity
    - Scope
    - Parent List
    - Title
    - Comment
    - Order
    - Completion
    as: new-todo-incomplete
  contexts:
    desktop:
      place: desktop-app::account
- text: When the absent incoming item belongs to an existing or newly created parent and its completion is
    complete, create it in that state
  kind: product
  entities:
  - entity: todo
    effect: creates
    to: Complete
    facts:
    - Identity
    - Scope
    - Parent List
    - Title
    - Comment
    - Order
    - Completion
    as: new-todo-complete
  contexts:
    desktop:
      place: desktop-app::account
- text: When the accepted live wim hof session record is absent locally, create its retained facts with defaults
    for unexchanged fields
  kind: product
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
    as: new-wim-hof-session
  contexts:
    desktop:
      place: desktop-app::account
- text: When the accepted live meditation session record is absent locally, create its retained facts with
    defaults for unexchanged fields
  kind: product
  entities:
  - entity: meditation-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Duration
    - Mood
    as: new-meditation-session
  contexts:
    desktop:
      place: desktop-app::account
- text: When the accepted live patterns session record is absent locally, create its retained facts with defaults
    for unexchanged fields
  kind: product
  entities:
  - entity: patterns-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Recorded duration values
    - Mood
    as: new-patterns-session
  contexts:
    desktop:
      place: desktop-app::account
- text: When the accepted live sun salutation session record is absent locally, create its retained facts with
    defaults for unexchanged fields
  kind: product
  entities:
  - entity: sun-salutation-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Repetitions
    - Mood
    as: new-sun-salutation-session
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted habit deletion marker, exclude the addressed active record while retaining its protocol
    tombstone
  kind: product
  entities:
  - entity: habit
    effect: removes
    as: deleted-habit
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted list deletion marker, exclude the addressed active record while retaining its protocol
    tombstone
  kind: product
  entities:
  - entity: list
    effect: removes
    as: deleted-list
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted incomplete deletion marker, exclude the addressed active record while retaining its
    protocol tombstone
  kind: product
  entities:
  - entity: todo
    effect: removes
    as: deleted-todo-incomplete
    from: Incomplete
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted completed deletion marker, exclude the addressed active record while retaining its
    protocol tombstone
  kind: product
  entities:
  - entity: todo
    effect: removes
    as: deleted-todo-complete
    from: Complete
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted wim hof session deletion marker, exclude the addressed active record while retaining
    its protocol tombstone
  kind: product
  entities:
  - entity: wim-hof-session
    effect: removes
    as: deleted-wim-hof-session
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted meditation session deletion marker, exclude the addressed active record while retaining
    its protocol tombstone
  kind: product
  entities:
  - entity: meditation-session
    effect: removes
    as: deleted-meditation-session
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted patterns session deletion marker, exclude the addressed active record while retaining
    its protocol tombstone
  kind: product
  entities:
  - entity: patterns-session
    effect: removes
    as: deleted-patterns-session
  contexts:
    desktop:
      place: desktop-app::account
- text: For an accepted sun salutation session deletion marker, exclude the addressed active record while retaining
    its protocol tombstone
  kind: product
  entities:
  - entity: sun-salutation-session
    effect: removes
    as: deleted-sun-salutation-session
  contexts:
    desktop:
      place: desktop-app::account
- text: After successful record application, finish exchange status and clear the pending review; the ordinary
    apply/ack savepoint rolls back record changes on failure
  kind: product
  entities:
  - entity: sync-settings
    effect: changes
    facts:
    - Exchange status
    - Retry status
    - Pending review
  contexts:
    desktop:
      place: desktop-app::account
references:
- kind: code
  role: implementation
  target: src/app/app_sync.zi
- kind: code
  role: implementation
  target: src/app/sync_retry.zi
- kind: code
  role: implementation
  target: src/storage/sync_review.zi
- kind: code
  role: implementation
  target: src/storage/storage_core.zi
- kind: code
  role: implementation
  target: src/storage/storage_core.zi#storage_apply_sync_response_json
- kind: code
  role: implementation
  target: src/storage/habit_sync_sql.zi
- kind: code
  role: implementation
  target: src/storage/sync_sql.zi
---

# Sync data — unattended

## Trigger

Sync data for pending current-identity changes.

## Outcome

Enabled current-account protocol-v6 exchange sends queued changes and applies accepted ordinary response/ack transactionally. Callback identity checks prevent applying another identity response; some status metadata lies outside the apply transaction.

## Decision points

### Incoming record state

What does an accepted incoming record describe?

- Existing live record → change only accepted exchanged fields under the implemented conflict checks.
- Absent live record → create its retained facts with local-only defaults.
- Deletion marker → exclude the addressed record from active history while retaining protocol tombstones.
