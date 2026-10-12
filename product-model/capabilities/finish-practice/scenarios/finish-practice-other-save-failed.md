---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: The originating timed or movement run reaches qualifying completion but its result save fails
  kind: condition
  unattended: true
  entities:
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Result values
    - Save outcome
    as: timed-meditation
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Result values
    - Save outcome
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Result values
    - Save outcome
  contexts:
    desktop:
      place: desktop-app
- text: If the selected family is meditation, retain its ordinary unsaved result without creating a saved record
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    to: Completed
    from: Running
    as: timed-meditation
  contexts:
    desktop:
      place: desktop-app::meditation
- text: For the alternative meditation process already Awaiting finish, an explicit Finish attempt with failed
    saving retains its unsaved result
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    to: Completed
    from: Awaiting finish
    as: waiting-meditation
  contexts:
    desktop:
      place: desktop-app::meditation
- text: If the selected family is patterns, retain its ordinary unsaved result without creating a saved record
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    to: Completed
    from: Running
  contexts:
    desktop:
      place: desktop-app::patterns
- text: If the selected family is sun salutation, retain its ordinary unsaved result without creating a saved
    record
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    to: Completed
    from: Running
  contexts:
    desktop:
      place: desktop-app::sun-salutation
- text: For a meditation result with Local Lumi origin, archive its recorded values with unsaved status and
    clear that result process instead of retaining ordinary results
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
  - entity: meditation-practice
    effect: removes
    from: Completed
    as: timed-meditation
  contexts:
    desktop:
      place: desktop-app::lumi
- text: For the alternative waiting Meditation result with Local Lumi origin, archive its values with unsaved
    status and clear that result instead of retaining ordinary results
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
  - entity: meditation-practice
    effect: removes
    from: Completed
    as: waiting-meditation
  contexts:
    desktop:
      place: desktop-app::lumi
- text: For a patterns result with Local Lumi origin, archive its recorded values with unsaved status and clear
    that result process instead of retaining ordinary results
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
  - entity: patterns-practice
    effect: removes
    from: Completed
  contexts:
    desktop:
      place: desktop-app::lumi
- text: For a sun salutation result with Local Lumi origin, archive its recorded values with unsaved status
    and clear that result process instead of retaining ordinary results
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
  - entity: sun-salutation-practice
    effect: removes
    from: Completed
  contexts:
    desktop:
      place: desktop-app::lumi
references:
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
  target: src/screens/lumi_screen.zi
---

# Finish practice — other save failed

## Trigger

Finish practice — other save failed.

## Outcome

The other practice families can retain an unsaved ordinary result after a save failure. Lumi summary reports unsaved status when its route handles that result; no saved record is fabricated.

## Decision points

### Result family

Which originating process reached completion?

- Meditation → retain its duration result with unsaved status.
- Breathing Patterns → retain its duration/cycle result with unsaved status.
- Sun Salutation → retain its repetition result with unsaved status.

## Edge cases

- A Lumi-origin result follows the summary handler, which archives the recorded values with unsaved status and clears the live result; it does not fabricate a saved session.
- Meditation save failure also applies when explicit Finish leaves Awaiting finish; an automatic duration check is not the only qualifying completion path.
