---
kind: primary
result: achieved
routes:
  desktop: Native desktop
steps:
- text: Request Breathing Patterns in Lumi
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
  - entity: patterns-practice
    effect: creates
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Ratio
    - Phase
    - Cycle
    - Duration
    - Elapsed progress
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
      place: desktop-app::patterns
- text: Reach configured normal completion
  kind: condition
  actor: user
  capability: finish-practice
  entities: []
  contexts:
    desktop:
      place: desktop-app::patterns
- text: Save qualifying recorded progress and retain the completed result
  kind: product
  actor: user
  capability: finish-practice
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    from: Running
    to: Completed
  - entity: patterns-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Recorded duration values
    - Mood
  contexts:
    desktop:
      place: desktop-app::patterns
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
  - entity: patterns-practice
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

# Complete Breathing Patterns with Lumi

## Trigger

User requests a new practice from Lumi and follows its normal completion path.

## Outcome

The conversation shows its recorded values and save outcome; the live result is cleared.
