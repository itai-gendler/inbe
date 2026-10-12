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
---

# Only the originating practice advances and saves its result

Observers display remote progress and request control without advancing origin time or creating duplicate results. Explicit pause differs from mobile/web background handling; desktop focus loss does not trigger that handling.
