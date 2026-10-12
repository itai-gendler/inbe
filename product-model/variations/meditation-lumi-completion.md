---
kind: configuration
of: journey-scenario
settings:
- entity: meditation-settings
  fact: Extension controls
takesEffect: The live completion check reads the current extension-control preference.
stability: Preference changes can affect an ongoing check; no immutable journey choice is captured.
alternatives:
- id: practice-with-lumi-meditation-auto
  selectedWhen: Extension controls are disabled at completion.
- id: practice-with-lumi-meditation-explicit
  selectedWhen: Extension controls are enabled and User explicitly finishes before summary return. Missing preference
    loads enabled extension controls.
references:
- kind: code
  role: implementation
  target: src/app/app_settings.zi
---

# Meditation with Lumi completion

The preference determines whether an explicit finish is needed before Lumi returns the summary.
