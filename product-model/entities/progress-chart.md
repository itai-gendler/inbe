---
domain: lumi
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Progress chart

An archived snapshot of stored progress, with its own chart facts.

## Information kept

- **Archive identity** — Address distinguishing this archived chart row.
- **Scope** — Account data context used to derive and retain the chart.
- **Message header** — Conversation header and time associated with the chart snapshot.
- **Metric** — Selected supported practice or Habit progress metric.
- **Date range** — Requested range of one through thirty-one days.
- **Dates** — Dates in the selected range, including zero-filled days without matching progress.
- **Snapshot values** — Values derived from stored scoped progress at creation and retained with the chart.
- **Deletion marker** — Marker excluding the selected chart from active archive history.
