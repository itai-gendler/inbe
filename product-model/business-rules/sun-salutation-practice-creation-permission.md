---
appliesTo:
- type: entity
  id: sun-salutation-practice
  effect: creates
references:
- kind: code
  role: implementation
  target: src/practices/sun_salutation/sun_salutation_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Sun Salutation practice creation

User starts a new originating run from its saved family settings; restoration reuses an existing run rather than creating a duplicate. The Lumi creation selector retains the installed-app and tool-mode checks.
