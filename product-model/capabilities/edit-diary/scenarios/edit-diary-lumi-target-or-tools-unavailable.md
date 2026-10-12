---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Edit diary for the selected date
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
    - Diary available
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The mapped append path is unavailable or unresolved; no document edit is performed.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/diary/diary.zi
- kind: code
  role: implementation
  target: src/screens/diary_screen.zi
- kind: code
  role: implementation
  target: src/cells/diary_store.zi
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi#LumiPerform
---

# Edit diary — lumi target or tools unavailable

## Trigger

Edit diary for the selected date.

## Outcome

The mapped append path is unavailable or unresolved; no document edit is performed.
