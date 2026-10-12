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
- text: Selected content is unsupported image data or exceeds the sixteen-MB attachment bound.
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
- text: Unsupported or oversized selected content is refused before attachment.
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

# Attach diary photo — invalid format

## Trigger

Attach diary photo for the selected date.

## Outcome

Unsupported or oversized selected content is refused before attachment.
