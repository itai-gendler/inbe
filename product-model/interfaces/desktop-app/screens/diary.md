---
entities:
- entity: diary-entry
  shows:
  - Date
  - Text
  - Document
  - Photo references
  - Document validity
  - Save outcome
  collects:
  - Text
  - Photo references
- entity: diary-photo
  shows:
  - Name
  - Content
  - Format
  - Byte size
references:
- kind: code
  role: implementation
  target: src/cells/diary_store.zi
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
---

# Diary

The selected dated document and retained image references, with eligible editing, document validity and save outcomes.
