---
kind: configuration
of: capability-scenario
settings:
- entity: meditation-settings
  fact: Extension controls
takesEffect: The preference is read at the live completion check, including after changes during a run.
stability: No immutable captured preference is promised; existing archived summaries remain records of their own completion.
alternatives:
- id: finish-practice-lumi-meditation-auto
  selectedWhen: Extension controls are disabled, so the run completes automatically at elapsed duration.
- id: finish-practice-lumi-meditation-explicit
  selectedWhen: Extension controls are enabled, so User must explicitly finish at elapsed duration. Missing preference
    loads enabled extension controls.
references:
- kind: code
  role: implementation
  target: src/app/app_settings.zi
---

# Meditation with Lumi completion

The extension-control preference changes whether User must explicitly finish at elapsed duration before Lumi returns the summary.
