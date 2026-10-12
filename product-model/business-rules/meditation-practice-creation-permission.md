---
appliesTo:
- type: entity
  id: meditation-practice
  effect: creates
references:
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Meditation practice creation

User starts a new originating run from its saved family settings; restoration reuses an existing run rather than creating a duplicate. The Lumi creation selector retains the installed-app and tool-mode checks.
