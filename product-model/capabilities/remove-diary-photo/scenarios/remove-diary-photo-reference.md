---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Remove diary photo for the selected date
  kind: actor
  entities:
  - entity: diary-photo
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: The eligible loaded document contains the selected retained-image reference; removing that reference does
    not delete the original image bytes.
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
  - entity: diary-photo
    effect: reads
    facts:
    - Name
    - Content
    - Format
    - Byte size
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: The selected reference is removed and the original retained bytes remain.
  kind: product
  entities:
  - entity: diary-entry
    effect: changes
    facts:
    - Document
    - Photo references
    - Save outcome
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

# Remove diary photo — reference

## Trigger

Remove diary photo for the selected date.

## Outcome

The selected reference is removed and the original retained bytes remain.
