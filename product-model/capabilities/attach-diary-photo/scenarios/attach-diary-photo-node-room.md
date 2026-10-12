---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Choose an image file to attach at the selected date
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: Cached node-media room is insufficient for the selected image under the implemented media-room check.
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
- text: Cached node-room validation rejects content exceeding available media room.
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

# Attach diary photo — node room

## Trigger

Attach diary photo for the selected date.

## Outcome

Cached node-room validation rejects content exceeding available media room.
