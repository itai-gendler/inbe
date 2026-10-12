---
domain: practices
relations:
- entity: sun-salutation-session
  verb: produces
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/practices/sun_salutation/sun_salutation_session.zi
- kind: code
  role: implementation
  target: src/app/account_activity.zi
---

# Sun Salutation practice

A live Sun Salutation process, including its ordinary result stage; an unsaved result is not a saved record.

## Information kept

- **Origin** — Originating device and launch context, distinguished as Local ordinary, Local Lumi or Observed device. Only the originating device advances and saves the run.
- **Activity identity** — Identity distinguishing the published live run from earlier runs.
- **Publication** — Time and active status of the most recent published activity observation.
- **Revision** — Published progress revision used when matching remote control.
- **Movement step** — Current movement step in the live sequence.
- **Repetition progress** — Completed repetitions and position within the current repetition.
- **Pause** — Explicit pause state of the originating process.
- **Result values** — Positive completed repetitions retained in the ordinary result stage.
- **Save outcome** — Observed save success or failure; it does not imply atomic rollback.
- **Pending control** — An outstanding pause or resume request for observed activity.
- **Control outcome** — Observed acknowledgement, refusal or expiry of a pending remote-control request.

## States

### Running

The originating process progresses unless explicitly paused.

### Paused

Explicit progression is paused.

### Completed

An ordinary result is retained until dismissal or conversation return.
