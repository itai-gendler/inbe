---
appliesTo:
- type: entity
  id: lumi-message
  effect: reads
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
permits:
- actors:
  - user
- unattended: true
---

# User reads current-context conversation history

Current-context archive reads use the ordinary history path. Invalid delegated identity/history is an authentication or availability refusal, not an additional human role.
