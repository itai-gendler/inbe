---
appliesTo:
- type: entity
  id: account
  effect: changes
references:
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Account change

User resolves a proposed credential switch or registers an alias. Request/transfer completion applies only in its current identity context; switch detection and replacement SQL have different record scopes.
