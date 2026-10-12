---
appliesTo:
- type: entity
  id: progress-chart
  effect: reads
references:
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
permits:
- actors:
  - user
  when:
  - entity: profile
    fact: Account access mode
    is-not: Delegated
---

# User in nondelegated mode reads progress chart

Interactive payloads are absent from delegated row rendering; ordinary archived text can remain visible.
