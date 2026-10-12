---
availability:
- place: desktop-app
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/app/launcher_policy.zi
- kind: code
  role: implementation
  target: src/cells/package_manager.zi
domain: apps
---

# Check app updates

Check and activate compatible verified package releases, retaining a working fallback when trial activation fails.
