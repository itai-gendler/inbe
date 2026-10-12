---
appliesTo:
- type: entity
  id: todo
  effect: removes
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Todo removal

User deletes an addressed incomplete or complete item, or its confirmed parent removal removes it dependently. SQL replacement and accepted deletion markers retain their actual transaction/tombstone scopes.
