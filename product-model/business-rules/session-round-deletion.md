---
appliesTo:
- type: entity
  id: wim-hof-session
- type: entity
  id: patterns-session
references:
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Last positive-value deletion removes the saved result

Removing one exposed Wim Hof/Patterns value replaces remaining values; removing the last positive value removes the record from active history. Meditation and Sun Salutation expose whole-record deletion, not this editor.
