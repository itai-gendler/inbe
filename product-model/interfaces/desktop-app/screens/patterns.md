---
entities:
- entity: patterns-settings
  shows:
  - Preset
  - Phase durations
  - Session duration
  collects:
  - Preset
  - Phase durations
  - Session duration
- entity: patterns-practice
  shows:
  - Origin
  - Activity identity
  - Publication
  - Revision
  - Ratio
  - Phase
  - Cycle
  - Duration
  - Elapsed progress
  - Pause
  - Result values
  - Save outcome
  - Pending control
  - Control outcome
- entity: patterns-session
  shows:
  - Identity
  - Local date
  - Local time
  - Source
  - Recorded duration values
  - Mood
  collects:
  - Mood
references:
- kind: code
  role: implementation
  target: src/practices/patterns/patterns_practice.zi
- kind: code
  role: implementation
  target: src/app/account_activity_view.zi#ActivityDrawRemote
---

# Breathing Patterns

The Breathing Patterns process: configuration, phase/cycle progression, pause and ordinary recorded results. An observed account run presents its published progress and requested control.
