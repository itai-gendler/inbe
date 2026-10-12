---
entities:
- entity: wim-hof-settings
  shows:
  - Rounds
  - Breaths
  - Speed
  - Progression
  - Start preference
  - Between-round pause
  - Animation
  collects:
  - Rounds
  - Breaths
  - Speed
  - Progression
  - Start preference
  - Between-round pause
  - Animation
- entity: wim-hof-practice
  shows:
  - Origin
  - Activity identity
  - Publication
  - Revision
  - Phase
  - Round
  - Breath
  - Retention progress
  - Pause
  - Result values
  - Save outcome
  - Pending control
  - Control outcome
- entity: wim-hof-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Retention values
  - Mood
  collects:
  - Mood
references:
- kind: code
  role: implementation
  target: src/practices/whm/whm_session.zi
- kind: code
  role: implementation
  target: src/app/account_activity_view.zi#ActivityDrawRemote
---

# Wim Hof

The Wim Hof process: guide and settings, breathing/retention progression, explicit controls and ordinary results. An observed account run presents published progress and requests control without advancing or saving the origin.
