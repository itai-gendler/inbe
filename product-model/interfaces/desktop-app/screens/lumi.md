---
entities:
- entity: lumi-message
  shows:
  - Archive identity
  - Scope
  - Speaker
  - Text
  - Time
  - Card payload
  - Deletion marker
  collects:
  - Text
- entity: progress-chart
  shows:
  - Archive identity
  - Scope
  - Message header
  - Metric
  - Date range
  - Dates
  - Snapshot values
  - Deletion marker
- entity: feedback-proposal
  shows:
  - Identity
  - Scope
  - Title
  - Message
  - Context
  - Decision
  collects:
  - Decision
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Lumi

Current or older conversation rows and input, stored-progress chart snapshots and proposed feedback decisions, with waiting and failure outcomes.
