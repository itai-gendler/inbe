---
appliesTo:
- type: entity
  id: diary-entry
  effect: changes
references:
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Diary entry change

User edits text or attachment references, including recognized Lumi append. Incoming record handling preserves account scope, and record/file writes are not universally atomic.
