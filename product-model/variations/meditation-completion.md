---
kind: configuration
of: capability-scenario
settings:
- entity: meditation-settings
  fact: Extension controls
takesEffect: The preference is read at the live completion check, including after changes during a run.
stability: No immutable captured preference is promised; existing saved results remain records of their own completion.
alternatives:
- id: finish-practice-normal-meditation-auto
  selectedWhen: Ordinary origin with extension controls disabled completes automatically.
- id: finish-practice-normal-meditation-explicit
  selectedWhen: Ordinary origin with extension controls enabled requires explicit completion. Missing preference
    loads enabled extension controls.
- id: finish-practice-lumi-meditation-auto
  selectedWhen: Lumi origin with extension controls disabled completes automatically.
- id: finish-practice-lumi-meditation-explicit
  selectedWhen: Lumi origin with extension controls enabled requires explicit completion. Missing preference loads
    enabled extension controls.
references:
- kind: code
  role: implementation
  target: src/app/app_settings.zi
---

# Meditation completion

The extension-control preference changes whether User must explicitly finish at elapsed duration. Origin supplies eligibility for each normal or Lumi result path.
