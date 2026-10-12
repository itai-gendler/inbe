---
domain: practices
relations:
- entity: patterns-session
  verb: produces
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/practices/patterns/patterns_practice.zi
- kind: code
  role: implementation
  target: src/app/account_activity.zi
---

# Breathing Patterns practice

A live Breathing Patterns process, including its ordinary result stage; an unsaved result is not a saved record.

## Information kept

- **Origin** — Originating device and launch context, distinguished as Local ordinary, Local Lumi or Observed device. Only the originating device advances and saves the run.
- **Activity identity** — Identity distinguishing the published live run from earlier runs.
- **Publication** — Time and active status of the most recent published activity observation.
- **Revision** — Published progress revision used when matching remote control.
- **Ratio** — Configured four-phase ratio used by this live breathing process.
- **Phase** — Current inhale, hold, exhale or hold phase.
- **Cycle** — Current cycle and progress through its phases.
- **Duration** — Configured total duration of this live process.
- **Elapsed progress** — Originating elapsed practice time used for progression and qualifying partial saves.
- **Pause** — Explicit pause state of the originating process.
- **Result values** — Recorded duration values retained in the ordinary result stage.
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
