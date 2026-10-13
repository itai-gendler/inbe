---
kind: primary
result: achieved
routes:
  desktop: Native desktop
steps:
- text: Request Meditation in Lumi
  kind: actor
  actor: user
  capability: start-practice
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
- text: Start the requested process in the conversation action
  kind: product
  actor: user
  capability: start-practice
  entities:
  - entity: meditation-practice
    effect: creates
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Duration
    - Remaining time
    - Elapsed progress
    - Extension state
    - Waiting state
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
    to: Running
  contexts:
    desktop:
      place: desktop-app::lumi
- text: Carry User into the originating process
  kind: product
  actor: user
  capability: start-practice
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
- text: Reach configured normal completion
  kind: condition
  actor: user
  capability: finish-practice
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
- text: Save qualifying recorded progress and retain the completed result
  kind: product
  actor: user
  capability: finish-practice
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    from: Running
    to: Completed
  - entity: meditation-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Duration
    - Mood
  contexts:
    desktop:
      place: desktop-app::meditation
- text: Archive the result summary and carry User back to Lumi
  kind: product
  actor: user
  capability: finish-practice
  entities:
  - entity: lumi-message
    effect: creates
    facts:
    - Archive identity
    - Scope
    - Speaker
    - Text
    - Time
    - Card payload
    - Deletion marker
  - entity: meditation-practice
    effect: removes
    from: Completed
  contexts:
    desktop:
      place: desktop-app::lumi
- text: Read the archived summary
  kind: actor
  actor: user
  capability: browse-conversation
  entities:
  - entity: lumi-message
    effect: reads
    facts:
    - Archive identity
    - Scope
    - Speaker
    - Text
    - Time
    - Card payload
    - Deletion marker
  contexts:
    desktop:
      place: desktop-app::lumi
references:
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/practices/practice_actions.zi
- kind: code
  role: implementation
  target: src/practices/session_results.zi
---

# Complete Meditation with Lumi

## Trigger

User requests a new practice from Lumi and follows its normal completion path.

## Outcome

The conversation shows its recorded values and save outcome; the live result is cleared.

## Decision points

### Extension controls

Does completion wait for an explicit finish?

- Extension controls disabled → the run completes automatically at elapsed duration.
- Extension controls enabled → the run waits at zero remaining duration until User chooses Finish.
