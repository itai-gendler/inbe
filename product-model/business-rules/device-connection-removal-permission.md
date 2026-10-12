---
appliesTo:
- type: entity
  id: device-connection
  effect: removes
references:
- kind: code
  role: implementation
  target: src/app/device_link_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Device connection removal

User cancellation or local expiry resets the transfer process. Removing this local process does not certify remote mailbox erasure or revoke credentials already received elsewhere.
