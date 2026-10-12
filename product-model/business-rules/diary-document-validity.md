---
appliesTo:
- type: entity
  id: diary-entry
references:
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
---

# Diary edits require eligible dates and valid loaded documents

Future dates, malformed versioned documents and incomplete record manifests prevent stale content overwrite. Record content is preferred to an older local-file fallback.
