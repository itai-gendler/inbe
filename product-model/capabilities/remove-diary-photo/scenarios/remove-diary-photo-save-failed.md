---
kind: edge
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
- text: The eligible loaded document contains the selected retained-image reference; removing that reference
    does not delete the original image bytes.
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
- text: If the complete date-record write fails, restore the previous presented document and report failure
    without claiming a completed reference removal
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: If the date-record write succeeds but the package-file write fails, retain its removed reference in
    the record while restoring the previous presented document; original photo bytes remain
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

# Remove diary photo — save failed

## Trigger

Remove diary photo for the selected date.

## Outcome

A failed reference save reports failure and restores the previous presented document; partial underlying record writes are not universally rolled back.

## Decision points

### Failed save stage

Which write failed?

- Complete date-record write → no completed reference removal is claimed.
- Package-file write after the record succeeds → the persisted record loses the reference despite the restored presentation; original bytes remain.
