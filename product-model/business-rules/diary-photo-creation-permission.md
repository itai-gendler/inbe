---
appliesTo:
- type: entity
  id: diary-photo
  effect: creates
references:
- kind: code
  role: implementation
  target: src/cells/diary_store.zi
permits:
- actors:
  - user
---

# User performs Diary photo creation

User attaches picker-selected supported image bytes within the size and cached-node-room bounds. Retained originals remain after a document reference is removed; attachment failure can leave already written bytes.
