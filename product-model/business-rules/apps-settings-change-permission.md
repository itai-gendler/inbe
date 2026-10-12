---
appliesTo:
- type: entity
  id: apps-settings
  effect: changes
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Apps settings change

User changes enabled/pinned app choices and ordering without deleting app data. Package verification, activation or fallback receipts update installed availability and release status; preference restoration does not restore account secrets.
