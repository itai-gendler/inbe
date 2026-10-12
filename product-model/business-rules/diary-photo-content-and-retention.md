---
appliesTo:
- type: entity
  id: diary-entry
- type: entity
  id: diary-photo
references:
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
- kind: code
  role: implementation
  target: src/cells/diary_store.zi
---

# Diary reference removal retains original attachment bytes

Attach only supported images within sixteen MB and cached node-media room. A reference removal changes the document without deleting original bytes. File and record writes can partially succeed.
