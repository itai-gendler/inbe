---
appliesTo:
- type: entity
  id: audio-settings
  effect: changes
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_audio.zi
permits:
- actors:
  - user
---

# User performs Audio settings change

User saves cue/music volumes, selected cues and per-practice music preferences. This operation does not imply custom-library import, download or platform playback acceptance.
