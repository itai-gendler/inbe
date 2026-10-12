---
domain: apps
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/cells/package_manager.zi
---

# Apps settings

App selection and installed-package availability; availability facts derive from enabled and installed masks.

## Information kept

- **Enabled apps** — App choices enabled in the local profile; disabling a choice retains its data.
- **Installed apps** — Packages currently installed and available to the host.
- **Pinned apps** — Enabled app choices pinned for direct access.
- **Pinned order** — Saved order of pinned app choices.
- **Setup selection** — Initial app choices accepted during setup.
- **Package versions** — Installed and available release versions for each inspected app package.
- **Package status** — Observed download, verification, trial, activation or fallback status.
- **Online Lumi** — Preference enabling account-backed online responses when the other request preconditions hold.
- **Lumi installed** — Whether the Lumi package is installed.
- **Habits available** — Whether Habits is enabled and installed.
- **Lists available** — Whether Lists is enabled and installed.
- **Diary available** — Whether Diary is enabled and installed.
- **Practices available** — Whether Practices is enabled and installed.
