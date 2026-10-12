---
appliesTo:
- type: entity
  id: meditation-settings
  effect: changes
references:
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Meditation settings change

User saves this family’s exposed configuration; supported restoration changes only demonstrated preferences. The fixed family choice is vocabulary, while its saved parameter facts remain specific to this family.
