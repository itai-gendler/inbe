---
appliesTo:
- type: entity
  id: account
  effect: removes
references:
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Account removal

User logs out or confirms remote clearing. Local setup is removed after the implemented operation or success receipt; retained local records and remote server retention have separate scopes.
