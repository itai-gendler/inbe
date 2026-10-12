---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Choose cue/music volumes and selections
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::audio
  actor: user
- text: The entered cue volume, music volume, cue choices and per-practice music selection are resolved against
    the exposed preferences.
  kind: condition
  entities:
  - entity: audio-settings
    effect: reads
    facts:
    - Cue volume
    - Music volume
    - Cue choices
    - Practice music
  contexts:
    desktop:
      place: desktop-app::audio
  actor: user
- text: The exposed audio preferences persist; this does not include custom library CRUD or delivery guarantees.
  kind: product
  entities:
  - entity: audio-settings
    effect: changes
    facts:
    - Cue volume
    - Music volume
    - Cue choices
    - Practice music
  contexts:
    desktop:
      place: desktop-app::audio
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_audio.zi
---

# Change audio settings — preferences

## Trigger

Choose cue/music volumes and selections.

## Outcome

The exposed audio preferences persist; this does not include custom library CRUD or delivery guarantees.
