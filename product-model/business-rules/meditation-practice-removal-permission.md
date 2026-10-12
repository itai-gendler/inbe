---
appliesTo:
- type: entity
  id: meditation-practice
  effect: removes
references:
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Meditation practice removal

User exits or dismisses the ordinary live/result process. Completion and Lumi-summary handling close only their demonstrated process path, preserving saved-record effects separately.
