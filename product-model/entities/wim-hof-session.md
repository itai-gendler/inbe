---
domain: practices
references:
- kind: code
  role: implementation
  target: src/practices/whm/whm_session.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Wim Hof session

An independently addressed saved Wim Hof result. Removal is from active history; synchronization tombstones may remain.

## Information kept

- **Identity** — Address distinguishing this saved result in active history and synchronization.
- **Local date** — Local calendar date recorded for this saved practice.
- **Local time** — Recorded local practice time displayed with the result.
- **Source** — Recorded origin/source of the saved practice, including imported records where supported.
- **Retention values** — Positive completed retention values; the exposed editor changes or removes individual values.
- **Mood** — Optional positive mood selected on an ordinary saved result; Lumi completion does not expose that result control.
