---
appliesTo:
- type: entity
  id: device-settings
  effect: changes
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_device.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Device settings change

User accepts initial language or saves the exposed native device preferences. Applicable preference restoration retains the demonstrated whitelist; desktop focus loss remains distinct from explicit practice pause.
