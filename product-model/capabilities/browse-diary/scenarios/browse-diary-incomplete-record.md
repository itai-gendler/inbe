---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Browse diary for the selected date
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: The dated record manifest is incomplete; a stale local-file fallback is not loaded for overwrite.
  kind: condition
  entities:
  - entity: diary-entry
    effect: reads
    facts:
    - Date
    - Text
    - Document
    - Photo references
    - Document validity
    - Save outcome
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: An incomplete record manifest does not fall back to stale local-file content for overwrite.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::diary
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
---

# Browse diary — incomplete record

## Trigger

Browse diary for the selected date.

## Outcome

An incomplete record manifest does not fall back to stale local-file content for overwrite.
