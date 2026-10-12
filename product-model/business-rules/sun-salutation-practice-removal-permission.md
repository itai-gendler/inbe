---
appliesTo:
- type: entity
  id: sun-salutation-practice
  effect: removes
references:
- kind: code
  role: implementation
  target: src/practices/sun_salutation/sun_salutation_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Sun Salutation practice removal

User exits or dismisses the ordinary live/result process. Completion and Lumi-summary handling close only their demonstrated process path, preserving saved-record effects separately.
