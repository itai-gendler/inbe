---
domain: practices
references:
- kind: code
  role: implementation
  target: src/practices/sun_salutation/sun_salutation_session.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Sun Salutation session

An independently addressed saved Sun Salutation result. Removal is from active history; synchronization tombstones may remain.

## Information kept

- **Identity** — Address distinguishing this saved result in active history and synchronization.
- **Local date** — Local calendar date recorded for this saved practice.
- **Local time** — Recorded local practice time displayed with the result.
- **Source** — Recorded origin/source of the saved practice, including imported records where supported.
- **Repetitions** — Recorded positive completed repetitions; this saved family has no matching round-value editor.
- **Mood** — Optional positive mood selected on an ordinary saved result; Lumi completion does not expose that result control.
