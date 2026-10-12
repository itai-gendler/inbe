---
appliesTo:
- type: entity
  id: habit-day
  effect: changes
  facts:
  - Stored count
  - Stored completion
  contexts:
  - place: desktop-app::habits
references:
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
permits:
- actors:
  - user
  when:
  - fact: Scheduled
    is: true
- actors:
  - user
  when:
  - fact: Completed
    is: true
---

# User changes ordinary stored progress on scheduled or completed days

The ordinary overview permits interaction when the date is scheduled or already derived completed. Lumi, detail handlers, import and incoming application are outside this selector.
