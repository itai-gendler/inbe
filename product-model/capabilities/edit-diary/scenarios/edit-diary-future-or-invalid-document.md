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
      place: desktop-app::diary
  actor: user
- text: The selected date is future or its loaded document is malformed or incomplete, so entered text cannot replace
    it.
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
- text: A future date or invalid loaded document prevents the edit from replacing content.
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

# Edit diary — future or invalid document

## Trigger

Edit diary for the selected date.

## Outcome

A future date or invalid loaded document prevents the edit from replacing content.
