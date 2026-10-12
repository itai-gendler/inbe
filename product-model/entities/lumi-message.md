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

# Lumi message

A retained non-chart conversation row.

## Information kept

- **Archive identity** — Address distinguishing this retained non-chart conversation row.
- **Scope** — Account data context containing the conversation archive.
- **Speaker** — Whether the row records User input or a Product reply.
- **Text** — Retained conversation text, including local replies and returned online text.
- **Time** — Retained row time used for archive chronology.
- **Card payload** — Supported non-chart card or reference content; delegated rendering strips interactive payloads.
- **Deletion marker** — Marker excluding the addressed row from active history while retaining its archive tombstone.
