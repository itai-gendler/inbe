---
appliesTo:
- type: entity
  id: patterns-practice
  effect: creates
references:
- kind: code
  role: implementation
  target: src/practices/patterns/patterns_practice.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Breathing Patterns practice creation

User starts a new originating run from its saved family settings; restoration reuses an existing run rather than creating a duplicate. The Lumi creation selector retains the installed-app and tool-mode checks.
