---
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_device.zi
---

# Device settings

Native device preferences.

## Information kept

- **Preferred language** — Saved language selection among the shipped locales.
- **System language** — Whether locale selection follows the system language rather than the explicit preference.
- **Orientation** — Preferred application orientation where the platform exposes it.
- **Fullscreen** — Saved native fullscreen preference.
- **Keyboard** — Preference for the exposed keyboard behavior.
- **Startup** — Saved choice controlling application startup behavior.
- **Close action** — Saved action used when the native application is closed.
- **Background play** — Preference governing supported background practice behavior; desktop focus loss does not itself pause a practice.
