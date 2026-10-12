---
appliesTo:
- type: entity
  id: lumi-message
- type: entity
  id: progress-chart
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
---

# Lumi archive operations preserve identity and payload validity

Current account/local scope, timestamps, valid payloads and deletion markers determine archived rows. Invalid history prevents rewrite; the synthetic greeting has no deletable archive identity.
