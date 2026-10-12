---
kind: primary
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
- text: The selected local date resolves a supported complete document; malformed structure or incomplete record
    content prevents editable stale fallback.
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
- text: The eligible date loads its versioned text/document and retained photo references.
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

# Browse diary — date

## Trigger

Browse diary for the selected date.

## Outcome

The eligible date loads its versioned text/document and retained photo references.
