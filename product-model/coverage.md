---
scope: Inspected native desktop product paths and Linux file effects at source commit 11324d6ece03d474f923c80d8a9493b8901d4c53.
method: Static entry-point, handler, persistence and permission tracing; read-only tracked-file inventory.
covered:
- description: Native entry, initial setup and inspected navigation
  paths:
  - src/main.zi
  - src/platform/app_host.zi
  - apps/inbe/
  - src/screens/language_screen.zi
  - src/screens/app_selection_screen.zi
  - src/app/app_launcher.zi
  - src/app/app_launcher_state.zi
  - src/app/app_nav_state.zi
- description: Four native practice families, results and saved maintenance
  paths:
  - apps/practice/
  - src/practices/
  - src/screens/habits/habit_session_screen.zi
  - src/storage/storage_sessions.zi
- description: Habit definitions, day derivation and inspected persistence/exchange
  paths:
  - apps/habits/
  - src/habits/
  - src/screens/habits/
  - src/screens/habits_screen.zi
  - src/storage/storage_habits.zi
  - src/storage/storage_habit_materialize.zi
  - src/storage/habit_sync_sql.zi
- description: List and Todo local mutation paths
  paths:
  - apps/lists/
  - src/screens/elist_screen.zi
  - src/storage/storage_elist.zi
- description: Diary date documents and selected attachment paths
  paths:
  - apps/diary/
  - src/screens/diary_screen.zi
  - src/cells/diary_store.zi
  - src/cells/diary_records.zi
- description: Lumi conversation, bounded online path, charts and feedback
  paths:
  - apps/lumi/
  - src/screens/lumi_screen.zi
  - src/cells/lumi_store.zi
  - src/cells/lumi_online.zi
  - src/cells/lumi_progress.zi
  - src/cells/feedback_store.zi
- description: Inspected account, node, review, retry, activity and transfer paths
  paths:
  - src/storage/sync_account.zi
  - src/storage/sync_nodes.zi
  - src/storage/sync_node_storage.zi
  - src/storage/sync_review.zi
  - src/storage/sync_async.zi
  - src/storage/storage_core.zi
  - src/app/app_sync.zi
  - src/app/sync_retry.zi
  - src/app/account_activity.zi
  - src/app/account_activity_model.zi
  - src/app/device_link_session.zi
  - src/screens/settings/settings_sync_account_impl.zi
  - src/app/account_activity_view.zi
  - src/storage/sync_sql.zi
- description: Native data selection and Linux archive effects
  paths:
  - src/screens/settings/settings_data_ui.zi
  - src/storage/import.zi
  - src/storage/export_sql.zi
  - src/storage/archive_file_linux.zi
- description: Appearance editing and installed-package update checks
  paths:
  - src/screens/settings/settings_appearance.zi
  - src/app/appearance_actions.zi
  - src/cells/package_manager.zi
  - src/cells/package_release.zi
- description: Inspected preference and cached social-reading paths and shipped locales
  paths:
  - src/screens/profile_screen.zi
  - src/screens/settings/settings_device.zi
  - src/screens/settings/settings_audio.zi
  - src/screens/settings/settings_notifications.zi
  - src/screens/profile_social.zi
  - src/screens/leaderboard_screen.zi
  - locales/
exclusions:
- description: Build, release, test and hook infrastructure
  paths:
  - .github/
  - .githooks/
  - scripts/
  - tests/
  - Makefile
  - makefile
  - GNUmakefile
  - fastlane/
- description: Design proposals and generated nonbehavioral output
  paths:
  - design/
  - output/
  - character-proposals/
unmapped:
- description: Android counterpart, scanner, services, push and lifecycle acceptance
  paths:
  - src/platform/android/
  - droid/
- description: Browser counterpart, storage and extension delivery
  paths:
  - src/platform/web_storage.zi
  - src/platform/web_bridge.zi
  - src/platform/web_window.zi
  - web-assets/
  - packaging/chrome-web-store/
  - packaging/firefox-addons/
- description: Complete Telegram and delegate contract and revocation
  paths:
  - src/storage/delegate_store.zi
  - src/storage/delegate_storage.zi
  - src/app/telegram_account_flow.zi
  - src/cells/lumi_telegram.zi
  - src/screens/settings/settings_telegram.zi
- description: Independent Harmony/MCP inbound acceptance, harness actors and tool access
  paths:
  - src/platform/host_actions.zi
  - src/platform/feature_request.zi
  - src/cells/app_tools.zi
  - assets/mcp/tools.json
- description: Terminal platform interaction and delivery
  paths:
  - src/platform/app_host.zi
- description: Desktop breaks and their settings
  paths:
  - src/breaks/
  - src/screens/settings/settings_breaks.zi
- description: Custom audio library, import/download/preview and platform effects
  paths:
  - src/app/audio_selection.zi
  - src/platform/audio_runtime.zi
  - src/practices/meditation/meditation_audio_archive.zi
- description: Actual notification scheduling and delivery
  paths:
  - src/app/notification_schedule.zi
  - src/app/app_notifications.zi
- description: Residual Diary history, spelling and media lifecycle
  paths:
  - src/cells/diary_history.zi
  - src/cells/diary_spelling.zi
  - src/cells/diary_records.zi
  - src/cells/diary_store.zi
- description: Social request and relationship mutation paths
  paths:
  - src/screens/profile_social.zi
  - src/storage/social_async.zi
- description: Residual node storage policy, quotas, payment and administration
  paths:
  - src/storage/sync_node_storage.zi
  - src/screens/profile_node_storage.zi
- description: Complete legacy schema/data upgrade preservation
  paths:
  - src/storage/schema.zi
  - src/storage/database_upgrade.zi
  - src/storage/root_upgrade.zi
  - src/app/settings_upgrade.zi
  - src/storage/import.zi
- description: Donation, wallet and public-site behavior
  paths:
  - src/app/app_donation.zi
  - src/app/donation_modal.zi
  - site/
- description: Full mini-mode and temporary-data contract
  paths:
  - src/app/mini_mode.zi
  - src/app/mini_mode_expand.zi
- description: Additional online/tool chains and complete custom-style tool behavior
  paths:
  - src/cells/lumi_online.zi
  - src/cells/app_tools.zi
- description: Untraced repeat-last-practice implementation suggested by documentation
  paths:
  - README.md
  - src/practices/practice_actions.zi
- description: Residual encrypted cell-record and preference replay acceptance beyond mapped SQL record outcomes
  paths:
  - src/storage/cell_records.zi
  - src/storage/storage_core.zi
  - src/storage/sync_sql.zi
  - src/cells/diary_records.zi
  - src/cells/lumi_store.zi
limitations:
- description: Native/Linux implementation does not settle other-platform file acceptance
  paths:
  - src/storage/archive_file_linux.zi
  - src/platform/app_host.zi
- description: Compiled Habit/practice host screens do not establish universal package-only updates
  paths:
  - src/screens/habits_screen.zi
  - src/practices/
  - src/cells/package_manager.zi
- description: Outbound service calls do not establish remote retention, convergence or operational delivery
  paths:
  - src/app/app_sync.zi
  - src/storage/sync_account.zi
  - src/app/device_link_session.zi
  - src/cells/lumi_online.zi
- description: Source scope predicates differ across loader, materialization and cell persistence
  paths:
  - src/storage/storage_sessions.zi
  - src/storage/storage_habit_materialize.zi
  - src/cells/diary_records.zi
  - src/cells/lumi_store.zi
- description: Documentation diverges from inspected online, retry and publication behavior
  paths:
  - README.md
  - docs/SYNC_RECOVERY.md
  - docs/ACCOUNT_ACTIVITY.md
- description: Case-colliding build-file checkout requires pinned Git-object reads
  paths:
  - Makefile
  - makefile
  - GNUmakefile
---

# Coverage
