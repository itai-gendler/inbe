---
entities:
- entity: apps-settings
  shows:
  - Enabled apps
  - Installed apps
  - Pinned apps
  - Pinned order
  - Setup selection
  - Package versions
  - Package status
  - Online Lumi
  - Lumi installed
  - Habits available
  - Lists available
  - Diary available
  - Practices available
  collects:
  - Enabled apps
  - Pinned apps
  - Pinned order
  - Setup selection
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/cells/package_manager.zi
---

# Apps

The app catalogue and selected/pinned choices, with installed package versions, pending installation and update status.
