---
appliesTo:
- type: entity
  id: device-connection
  effect: creates
references:
- kind: code
  role: implementation
  target: src/app/device_link_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Device connection creation

User starts desktop sending or receiving, determined by locally available credentials. Protocol preparation establishes the displayed code, comparison and local lifetime.
