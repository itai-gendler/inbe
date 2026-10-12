---
appliesTo:
- type: entity
  id: diary-entry
  effect: reads
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
    fact: Diary available
    is: true
---

# User with mapped Lumi tools performs diary entry reading

The mapped Lumi path requires nondelegated tool mode, installed Lumi and enabled/installed Diary. This selector does not claim the separate Harmony entry has identical checks.
