---
kind: edge
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
- text: The selected date is not future and its loaded versioned document is complete and valid before the
    entered text or references are saved.
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
- text: When the complete record write fails, report the failure without claiming a successfully saved date
    document
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: When a first complete date-record write succeeds but the later package-file write fails, retain that
    new record while reporting failure and restoring the previous presented edit
  kind: product
  entities:
  - entity: diary-entry
    effect: creates
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
- text: When an existing complete date-record write succeeds but the later package-file write fails, retain
    its changed content while reporting failure and restoring the previous presented edit
  kind: product
  entities:
  - entity: diary-entry
    effect: changes
    facts:
    - Text
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

# Edit diary — save failed

## Trigger

Edit diary for the selected date.

## Outcome

A record or package-file failure is reported; an earlier record write may already exist and no universal rollback is promised.

## Decision points

### Failed write stage

Which persisted effect preceded the failure?

- Complete record write fails → no successfully saved date document is claimed.
- Complete first record succeeds, package file fails → the record exists despite the restored presentation and failure notice.
- Existing record succeeds, package file fails → persisted content can differ from the restored presentation.
