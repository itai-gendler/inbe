---
domain: practices
references:
- kind: code
  role: implementation
  target: src/practices/patterns/patterns_practice.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Breathing Patterns session

An independently addressed saved Breathing Patterns result. Removal is from active history; synchronization tombstones may remain.

## Information kept

- **Identity** — Address distinguishing this saved result in active history and synchronization.
- **Local date** — Local calendar date recorded for this saved practice.
- **Local time** — Recorded local practice time displayed with the result.
- **Source** — Recorded origin/source of the saved practice, including imported records where supported.
- **Recorded duration values** — Positive recorded durations; the exposed editor changes or removes values and partial saves require at least sixty elapsed seconds.
- **Mood** — Optional positive mood selected on an ordinary saved result; Lumi completion does not expose that result control.
