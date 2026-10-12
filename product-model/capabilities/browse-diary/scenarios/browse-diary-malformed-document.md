---
kind: validation
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
- text: The loaded dated document has malformed or unsupported structure, so it is not a valid editable document.
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
- text: Malformed structure blocks a valid editable document and prevents a stale-content overwrite.
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

# Browse diary — malformed document

## Trigger

Browse diary for the selected date.

## Outcome

Malformed structure blocks a valid editable document and prevents a stale-content overwrite.
