---
entities:
- entity: meditation-settings
  shows:
  - Duration mode
  - Custom minutes
  - Interval bell
  - Extension controls
  collects:
  - Duration mode
  - Custom minutes
  - Interval bell
  - Extension controls
- entity: meditation-practice
  shows:
  - Origin
  - Activity identity
  - Publication
  - Revision
  - Duration
  - Remaining time
  - Elapsed progress
  - Extension state
  - Waiting state
  - Pause
  - Result values
  - Save outcome
  - Pending control
  - Control outcome
- entity: meditation-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Duration
  - Mood
  collects:
  - Mood
references:
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
- kind: code
  role: implementation
  target: src/app/account_activity_view.zi#ActivityDrawRemote
---

# Meditation

The Meditation process: configuration, duration countdown, pause, extension or awaiting Finish, and ordinary results. An observed account run presents published progress and requested control rather than originating time.
