---
appliesTo:
- type: entity
  id: diary-entry
  effect: creates
references:
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Diary entry creation

User first saves an eligible dated document or performs its first supported append. Incoming date-document application is account-scoped; malformed or incomplete record content does not license stale-file overwrite.
