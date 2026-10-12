---
appliesTo:
- type: entity
  id: device-connection
  effect: changes
references:
- kind: code
  role: implementation
  target: src/app/device_link_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Device connection change

User confirms comparison or Product polling/receipts progress the current transfer. Received and Connected are local stages; account-switch confirmation can remain pending after a receiver success observation.
