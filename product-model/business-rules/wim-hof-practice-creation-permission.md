---
appliesTo:
- type: entity
  id: wim-hof-practice
  effect: creates
references:
- kind: code
  role: implementation
  target: src/practices/whm/whm_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Wim Hof practice creation

User starts a new originating run from its saved family settings; restoration reuses an existing run rather than creating a duplicate. The Lumi creation selector retains the installed-app and tool-mode checks.
