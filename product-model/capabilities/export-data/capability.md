---
availability:
- place: desktop-app
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_data_ui.zi
- kind: code
  role: implementation
  target: src/storage/import.zi
- kind: code
  role: implementation
  target: src/storage/export_sql.zi
- kind: code
  role: implementation
  target: src/storage/archive_file_linux.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
domain: data
---

# Export data

Publish a SQLite database ZIP snapshot or undeleted-session CSV.
