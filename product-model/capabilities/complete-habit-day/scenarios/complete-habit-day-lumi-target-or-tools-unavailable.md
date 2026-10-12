---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to complete the referenced day
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: If current mode, installed Lumi or the required target app makes this tool unavailable, refuse before
    reading protected target data. An unresolved request with available tools follows only its permitted lookup
    branch and still performs no mutation.
  kind: condition
  entities:
  - entity: profile
    effect: reads
    facts:
    - Account access mode
  - entity: apps-settings
    effect: reads
    facts:
    - Lumi installed
    - Habits available
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Only with nondelegated tool mode, installed Lumi and the required target app available, attempt the
    bounded target lookup; an absent or unresolved target stops the action without mutation.
  kind: condition
  actor: user
  entities:
  - entity: habit
    effect: reads
    facts:
    - Identity
    - Name
    - Counting mode
    - Target
    - Practice links
  - entity: habit-day
    effect: reads
    facts:
    - Date
    - Stored count
    - Stored completion
    - Visible linked count
    - Effective count
    - Completed
  contexts:
    desktop:
      place: desktop-app::lumi
- text: The requested target cannot be resolved or the mapped tool path is unavailable; no day completion is
    performed.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
- kind: code
  role: implementation
  target: src/habits/habit_sessions.zi
- kind: code
  role: implementation
  target: src/storage/storage_habit_materialize.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi#LumiPerform
---

# Complete habit day — lumi target or tools unavailable

## Trigger

Complete habit day for the selected definition or date.

## Outcome

The requested target cannot be resolved or the mapped tool path is unavailable; no day completion is performed.
