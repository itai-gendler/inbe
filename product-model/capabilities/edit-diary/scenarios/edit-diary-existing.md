---
kind: primary
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
- text: The selected date is not future and its loaded versioned document is complete and valid before the entered
    text or references are saved.
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
- text: The eligible date document is saved. First save creates the date record; later editing changes it.
  kind: product
  entities:
  - entity: diary-entry
    effect: changes
    facts:
    - Text
    - Document
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

# Edit diary — existing

## Trigger

Edit diary for the selected date.

## Outcome

The eligible date document is saved. First save creates the date record; later editing changes it.
