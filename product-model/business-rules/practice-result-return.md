---
appliesTo:
- type: entity
  id: wim-hof-practice
- type: entity
  id: meditation-practice
- type: entity
  id: patterns-practice
- type: entity
  id: sun-salutation-practice
- type: entity
  id: lumi-message
references:
- kind: code
  role: implementation
  target: src/practices/whm/whm_session.zi
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
- kind: code
  role: implementation
  target: src/practices/patterns/patterns_practice.zi
- kind: code
  role: implementation
  target: src/practices/sun_salutation/sun_salutation_session.zi
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
---

# Normal results and Lumi summaries have different return effects

Ordinary completion retains a result stage. Lumi-origin normal completion archives saved/unsaved summary facts and clears that result process. Partial exits return to start without that summary.
