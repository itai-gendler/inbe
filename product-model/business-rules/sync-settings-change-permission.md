---
appliesTo:
- type: entity
  id: sync-settings
  effect: changes
references:
- kind: code
  role: implementation
  target: src/app/app_sync.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Sync settings change

User enables or requests exchange and makes keep, merge or replace decisions. Current-identity exchange, review and retry progression updates observable status; callback identity and protocol checks remain request constraints.
