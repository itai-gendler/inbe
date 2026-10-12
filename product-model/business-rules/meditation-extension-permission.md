---
appliesTo:
- type: entity
  id: meditation-practice
  effect: changes
  facts:
  - Duration
  contexts:
  - place: desktop-app::meditation
  to: Running
references:
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
permits:
- actors:
  - user
  when:
  - entity: meditation-settings
    fact: Extension controls
    is: true
---

# User with extension controls changes Meditation duration

Duration-extension edits require the related extension-control preference. Timer countdown changes remaining time rather than this configured-duration field.
