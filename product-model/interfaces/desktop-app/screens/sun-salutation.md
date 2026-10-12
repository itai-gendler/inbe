---
entities:
- entity: sun-salutation-settings
  shows:
  - Repetitions
  - Start timing
  - End timing
  - Character
  collects:
  - Repetitions
  - Start timing
  - End timing
  - Character
- entity: sun-salutation-practice
  shows:
  - Origin
  - Activity identity
  - Publication
  - Revision
  - Movement step
  - Repetition progress
  - Pause
  - Result values
  - Save outcome
  - Pending control
  - Control outcome
- entity: sun-salutation-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Repetitions
  - Mood
  collects:
  - Mood
references:
- kind: code
  role: implementation
  target: src/practices/sun_salutation/sun_salutation_session.zi
- kind: code
  role: implementation
  target: src/app/account_activity_view.zi#ActivityDrawRemote
---

# Sun Salutation

The Sun Salutation process: guide, repetition/timing/character settings, movement progression, pause and ordinary results. An observed account run presents published movement progress and requested control.
