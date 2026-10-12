---
appliesTo:
- type: entity
  id: appearance-settings
  effect: changes
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
permits:
- actors:
  - user
---

# User performs Appearance settings change

User saves appearance preferences at settings or selects a recognized theme or mode through Lumi. The Lumi-context Rule adds its implemented tool-mode gate; source parsing and save/readback are constraints rather than privileges.
