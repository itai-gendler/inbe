---
appliesTo:
- type: entity
  id: sun-salutation-practice
  effect: creates
  contexts:
  - place: desktop-app::lumi
references:
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/cells/app_tools.zi
permits:
- actors:
  - user
  when:
  - entity: profile
    fact: Account access mode
    is-not: Delegated
  - entity: apps-settings
    fact: Lumi installed
    is: true
  - entity: apps-settings
    fact: Practices available
    is: true
---

# User with mapped Lumi tools performs sun salutation practice creation

The mapped Lumi path requires nondelegated tool mode, installed Lumi and enabled/installed Practices. This selector does not claim the separate Harmony entry has identical checks.
