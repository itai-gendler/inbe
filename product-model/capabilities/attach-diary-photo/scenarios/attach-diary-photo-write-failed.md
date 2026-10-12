---
kind: edge
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
- text: The selected date document is eligible for editing, and selected image format, byte size and cached
    media room are checked before attachment.
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
    as: addressed-date
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: If exclusive file creation, complete write, sync or close fails, report attachment failure and attempt
    removal of that file; no complete retained photo is claimed
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: When the complete image file is retained but its record write or later document save fails, keep those
    named original bytes even though the attachment reports failure
  kind: product
  entities:
  - entity: diary-photo
    effect: creates
    facts:
    - Name
    - Content
    - Format
    - Byte size
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: If the complete first date-document record including the new reference writes successfully but its
    package file fails, retain that record while restoring the previous presented document
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
    as: first-date-record
  contexts:
    desktop:
      place: desktop-app::diary
  actor: user
- text: If an existing complete date-document record including the reference writes successfully but its package
    file fails, retain the changed references while restoring the previous presentation
  kind: product
  entities:
  - entity: diary-entry
    effect: changes
    facts:
    - Document
    - Photo references
    - Save outcome
    as: existing-date-record
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

# Attach diary photo — write failed

## Trigger

Attach diary photo for the selected date.

## Outcome

File/record/reference failure is reported. Newly written bytes may remain orphaned; an unchanged document view is not proof of atomic storage rollback.

## Decision points

### Failed attachment stage

What was retained before failure?

- File creation or completion fails → attempt file removal; no complete photo is claimed.
- Complete file succeeds and a later record or document write fails → retain the named original bytes, possibly without a document reference.
- Complete date record succeeds before package-file failure → retain its new reference despite the restored document presentation.
