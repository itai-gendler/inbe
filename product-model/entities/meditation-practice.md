---
domain: practices
relations:
- entity: meditation-session
  verb: produces
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
- kind: code
  role: implementation
  target: src/app/account_activity.zi
---

# Meditation practice

A live Meditation process, including its ordinary result stage; an unsaved result is not a saved record.

## Information kept

- **Origin** — Originating device and launch context, distinguished as Local ordinary, Local Lumi or Observed device. Only the originating device advances and saves the run.
- **Activity identity** — Identity distinguishing the published live run from earlier runs.
- **Publication** — Time and active status of the most recent published activity observation.
- **Revision** — Published progress revision used when matching remote control.
- **Duration** — Configured live duration, increased by an accepted extension.
- **Remaining time** — Time remaining before the duration check reaches completion or awaiting finish.
- **Elapsed progress** — Elapsed originating practice time used for qualifying partial saves.
- **Extension state** — Accepted extension progress of the live duration.
- **Waiting state** — Whether elapsed duration is waiting for explicit Finish or another extension.
- **Pause** — Explicit pause state of the originating process.
- **Result values** — Completed or elapsed duration retained in the ordinary result stage.
- **Save outcome** — Observed save success or failure; it does not imply atomic rollback.
- **Pending control** — An outstanding pause or resume request for observed activity.
- **Control outcome** — Observed acknowledgement, refusal or expiry of a pending remote-control request.

## States

### Running

The originating process progresses unless explicitly paused.

### Paused

Explicit progression is paused.

### Awaiting finish

Time has elapsed and extension controls require an explicit completion or extension.

### Completed

An ordinary result is retained until dismissal or conversation return.
