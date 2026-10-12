---
appliesTo:
- type: entity
  id: profile
  effect: changes
references:
- kind: code
  role: implementation
  target: src/screens/profile_screen.zi
permits:
- actors:
  - user
---

# User performs Profile change

User saves local display name, intention or selected picture. Name and intention commits retain the exposed byte/codepoint bounds; setup and received status do not establish a human-owner role.
