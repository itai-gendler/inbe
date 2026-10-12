---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Send message for the current conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Bounded nonempty composer input is resolved locally before online fallback; online use checks the current
    credential context, enabled preference and idle request state.
  kind: condition
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
  actor: user
- text: Input and the local reply are archived. Recognized actions dispatch to their own capabilities rather than
    hiding mutations inside chat.
  kind: product
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
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/lumi/lumi.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/cells/lumi_online.zi
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
---

# Send message — local response

## Trigger

Send message for the current conversation.

## Outcome

Input and the local reply are archived. Recognized actions dispatch to their own capabilities rather than hiding mutations inside chat.
