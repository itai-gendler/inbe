---
entities:
- entity: profile
  shows:
  - Local data context
  - Display name
  - Intention
  - Picture
  - Setup progress
  - Local counts
  - Account access mode
- entity: sync-settings
  shows:
  - Enabled
  - Exchange status
  - Retry status
  - Pending review
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_data_ui.zi
---

# Data

Local record counts and archive import, Linux-backed export and practice/Habit clearing outcomes, with available pending-change previews.
