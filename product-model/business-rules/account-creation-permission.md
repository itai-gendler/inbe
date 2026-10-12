---
appliesTo:
- type: entity
  id: account
  effect: creates
references:
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Account creation

User generates or imports local credentials or starts desktop credential transfer. Preparation and transfer receipts create available local setup only along the demonstrated installation path; a proposed switch waits for its local decision.
