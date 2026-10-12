---
domain: lumi
relations:
- entity: feedback-report
  verb: produces
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
---

# Feedback proposal

A kept feedback draft awaiting a human decision.

## Information kept

- **Identity** — Address of the kept draft selected for the human acceptance or dismissal decision.
- **Scope** — Current account data context containing the draft.
- **Title** — Feedback title kept while the draft is Proposed, bounded to 160 bytes.
- **Message** — Feedback body kept while the draft is Proposed, bounded to 4096 bytes.
- **Context** — Included product context kept while Proposed, bounded to 2048 bytes.
- **Decision** — Accepted or dismissed marker replacing the draft body after its decision write succeeds.

## States

### Proposed

Title, message and context remain available for the human decision.

### Accepted

The report was queued and the accepted marker replaced the draft body.

### Dismissed

The dismissed marker replaced the draft body without queueing a report.
