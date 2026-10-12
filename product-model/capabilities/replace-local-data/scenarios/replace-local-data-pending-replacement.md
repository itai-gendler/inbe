---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Replace local data for pending current-identity changes
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: A current-identity pending response is present; replacement clears the implemented SQL data scope before
    applying the snapshot within its savepoint.
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
    - Alias
    - Proposed identity
    - Installed identity
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Within the replacement savepoint, clear the existing SQL practice, dated progress, parent/item and
    social-cache scope together with its outbox; cell documents and preferences are not universally cleared
  kind: product
  entities:
  - entity: habit
    effect: removes
    as: cleared-habit
  - entity: habit-day
    effect: removes
    with: cleared-habit
    as: cleared-habit-day
  - entity: list
    effect: removes
    as: cleared-list
  - entity: todo
    effect: removes
    with: cleared-list
    as: cleared-incomplete-item
    from: Incomplete
  - entity: todo
    effect: removes
    with: cleared-list
    as: cleared-complete-item
    from: Complete
  - entity: wim-hof-session
    effect: removes
    as: cleared-wim-hof-session
  - entity: meditation-session
    effect: removes
    as: cleared-meditation-session
  - entity: patterns-session
    effect: removes
    as: cleared-patterns-session
  - entity: sun-salutation-session
    effect: removes
    as: cleared-sun-salutation-session
  - entity: friend
    effect: removes
  - entity: friend-request
    effect: removes
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
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
  actor: user
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
  actor: user
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
  actor: user
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
  actor: user
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
  actor: user
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
  actor: user
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
  actor: user
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
  actor: user
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
  actor: user
- text: After successful record application, finish exchange status and clear the pending review; the ordinary
    apply/ack savepoint rolls back record changes on failure
  kind: product
  entities:
  - entity: sync-settings
    effect: changes
    facts:
    - Pending review
    - Exchange status
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
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

# Replace local data — pending replacement

## Trigger

Replace local data for pending current-identity changes.

## Outcome

The pending response uses the implemented replacement path, whose clearing scope differs from local clear and account-switch detection. Pending review clears on successful application.

## Decision points

### Incoming record state

What does an accepted incoming record describe?

- Existing live record → change only accepted exchanged fields under the implemented conflict checks.
- Absent live record → create its retained facts with local-only defaults.
- Deletion marker → exclude the addressed record from active history while retaining protocol tombstones.
