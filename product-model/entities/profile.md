---
relations:
- entity: device-settings
  verb: has
  cardinality: one-to-one
- entity: apps-settings
  verb: has
  cardinality: one-to-one
- entity: appearance-settings
  verb: has
  cardinality: one-to-one
- entity: audio-settings
  verb: has
  cardinality: one-to-one
- entity: sync-settings
  verb: has
  cardinality: one-to-one
- entity: notifications-settings
  verb: has
  cardinality: one-to-one
- entity: wim-hof-settings
  verb: has
  cardinality: one-to-one
- entity: meditation-settings
  verb: has
  cardinality: one-to-one
- entity: patterns-settings
  verb: has
  cardinality: one-to-one
- entity: sun-salutation-settings
  verb: has
  cardinality: one-to-one
- entity: custom-appearance
  verb: has
  cardinality: one-to-one
- entity: account
  verb: has
  cardinality: one-to-one
- entity: habit
  verb: retains
  cardinality: one-to-many
- entity: list
  verb: retains
  cardinality: one-to-many
- entity: diary-entry
  verb: retains
  cardinality: one-to-many
- entity: lumi-message
  verb: retains
  cardinality: one-to-many
- entity: progress-chart
  verb: retains
  cardinality: one-to-many
- entity: feedback-proposal
  verb: retains
  cardinality: one-to-many
- entity: feedback-report
  verb: retains
  cardinality: one-to-many
- entity: friend
  verb: retains
  cardinality: one-to-many
- entity: friend-request
  verb: retains
  cardinality: one-to-many
- entity: sync-node
  verb: retains
  cardinality: one-to-many
- entity: device-connection
  verb: retains
  cardinality: one-to-many
- entity: wim-hof-practice
  verb: retains
  cardinality: one-to-many
- entity: wim-hof-session
  verb: retains
  cardinality: one-to-many
- entity: meditation-practice
  verb: retains
  cardinality: one-to-many
- entity: meditation-session
  verb: retains
  cardinality: one-to-many
- entity: patterns-practice
  verb: retains
  cardinality: one-to-many
- entity: patterns-session
  verb: retains
  cardinality: one-to-many
- entity: sun-salutation-practice
  verb: retains
  cardinality: one-to-many
- entity: sun-salutation-session
  verb: retains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/screens/profile_screen.zi
---

# Profile

The current local profile and its identity preferences.

## Information kept

- **Local data context** — Current local data context used by account-scoped records; it does not assert human ownership.
- **Display name** — Locally saved name shown for the profile.
- **Intention** — Locally saved intention text.
- **Picture** — Locally selected profile picture preference.
- **Setup progress** — Whether initial language and app-selection setup has been completed.
- **Local counts** — Derived counts of available local practice and Habit records.
- **Account access mode** — Current local, account-key or delegated mode.
