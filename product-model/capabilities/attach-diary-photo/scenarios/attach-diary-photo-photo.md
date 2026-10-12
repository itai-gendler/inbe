---
kind: primary
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
- text: Retain the validated selected image under its safe original name
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
- text: If this is the first complete save for the selected date, create its document with the new photo reference
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
- text: If a dated record already exists, persist its document with the added photo reference
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

# Attach diary photo — photo

## Trigger

Attach diary photo for the selected date.

## Outcome

Supported image bytes of at most sixteen MB are retained and their safe reference is added to the eligible document.

## Decision points

### Dated record

Did the date already have a complete saved document?

- Missing → create its first complete document including the reference.
- Existing → change its saved document references.
