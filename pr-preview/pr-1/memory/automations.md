# Automations Registry

*Auto-generated from live system data. Last updated: 2026-04-18 17:00 AST.*

**RULE: Every cron/automation change MUST be documented here.**

---

## Boot Hook (BOOT.md)

| Task | Purpose |
|------|---------|
| Per-channel model overrides | Re-applies Discord model overrides on every gateway restart: #opus → Opus, #manuals → Opus, #random → GPT-4o. Uses `session_status` per session key. |

## Self-Monitoring

| Job | Schedule | Purpose |
|-----|----------|---------|
| Cron Health Monitor | 9am/9pm daily | Checks ALL cron jobs for consecutiveErrors ≥ 2, alerts Will directly. Removes reliance on heartbeat manual check. |

## LaunchAgents (Local)

| Label | Script | Schedule | Purpose |
|-------|--------|----------|---------|
| `com.po.taildrop-watcher` | `scripts/taildrop_watcher.sh` | Always-on (KeepAlive) | Auto-receives Taildrop files to `~/Downloads/Taildrop/` |
| `ai.openclaw.tailscale-health` | `scripts/tailscale_health.sh` | Every 5 min | Checks Tailscale is Running. Auto-recovers if down (NO `--reset` flag — was causing duplicate nodes). Writes `tailscale_down_trigger.txt` on failure to wake Po. Alerts Discord #automations on failure. Zero AI. |
| `ai.openclaw.fleet-map-watcher` | `scripts/fleet-map-watcher.sh` | Always-on (KeepAlive) | Watches vault Helicopters/Missions/Pilots for .md changes → 5 min debounce → generate.py → git push. Uses kqueue_monitor for iCloud. Zero AI. |

## Cron Jobs (OpenClaw)

| Agent | Name | Schedule | Last Run | Errors | Purpose |
|-------|------|----------|----------|--------|---------|
| main | Community Scout - Weekly OpenClaw Ecosystem Scan | `0 8 * * 0` (Asia/Riyadh) | 2026-03-29 08:00 | 🟡 1 | You are the Community Scout |
| main | FedEx Package Tracker 399852099123 | `0 9 * * *` (Asia/Riyadh) | 2026-03-31 09:00 | 0 | FedEx tracking for package 399852099123 (Netherlands → Riyadh) |
| main | Kids Problem-Solving Challenge | `0 8 * * 4` (Asia/Riyadh) | 2026-03-26 08:00 | 🔴 3 | Generate 2-3 fresh activity ideas for Will's boys (ages 6-7) → deliver to main session. |
| main | Memory Cleanup | `0 6 * * 1` (Asia/Riyadh) | 2026-03-30 06:00 | 0 | MEMORY MAINTENANCE: Read /Users/willy/ |
| main | Monthly Self-Audit | `0 9 1 * *` (Asia/Riyadh) | Never | 0 | You are Po running a monthly self-audit |
| main | Morning Health Brief | `30 8 * * *` (Asia/Riyadh) | 2026-04-01 08:30 | 0 | Read the file ~/Library/Mobile Documents/com~apple~CloudDocs/Clawdrop/Health Check/health_export |
| main | Reminder: Share new giving ideas with Will | Every 10080 min | 2026-03-30 20:00 | 0 |  |
| main | Tailscale auth key rotation reminder | One-shot: 2026-06-20T06:00:00.000Z | Never | 0 |  |
| main | Weekly Skill Audit | `0 9 * * 6` (Asia/Riyadh) | 2026-03-28 09:00 | 0 | Run the weekly skill audit: execute `python3 scripts/skill_audit |
| main | whatsapp-watchdog | `*/30 * * * *` (Asia/Riyadh) | 2026-04-01 08:30 | 0 | Silent dry-run send to test WhatsApp connection → if dead, auto-restart gateway. |
| ops | Duty Roster Check | `30 14 * * *` (Asia/Riyadh) | 2026-03-31 14:30 | 0 | **LaunchAgent PAUSED** (2026-04-04). Backup check — Read OneDrive Excel → compare mtime → if changed: parse rotations → patch dashboard → git push. |
| ops | Ops Plan Pipeline | `45 17 * * *` (Asia/Riyadh) | 2026-04-05 13:43 | 0 | **Model: Claude Sonnet 4** (`anthropic/claude-sonnet-4-20250514`). Check Mail.app for new ops plan → vision-read FSR → update helicopter notes + flights. **H125 ONLY** (HZHC52-70, HZTH50-70). Fleet map regen handled by watcher (zero AI). Delivery: Discord #ops. 5pm run: mandatory EOD location update. |
| security | Agent Activity Audit | `0 10,22 * * *` (Asia/Riyadh) | 2026-03-31 22:00 | 🟡 1 | Run agent-audit.py → scan session logs for suspicious activity → flag HIGH/CRITICAL findings → update security state. |
| security | Weekly Security Audit | `0 2 * * 0` (Asia/Riyadh) | 2026-03-29 02:00 | 0 | Full system audit — firewall, ports, SSH, encryption, updates, agent session logs → email report to Will. |
| sfla | SFLA Combined Sync (UAM + Malham) | `0 19 * * *` (Asia/Riyadh) | 2026-03-31 19:00 | 0 | Daily SFLA sync for BOTH trackers |
| sfla | Monthly SFLA Report Reminders | Apple Reminders (Short term) | — | — | 8 reminders added 2026-04-09: May–Dec 2026. Will runs `run_report.sh` himself each month, sends to POI, marks done. |

## LaunchAgents (macOS launchd — zero AI tokens)

| Label | Trigger | Script | Purpose |
|-------|---------|--------|---------|
| ai.openclaw.ceo-dashboard | Always running | ceo_dashboard_server.sh |  |
| ai.openclaw.chrome-allow | WatchPaths (file change) | gateway_post_start.sh | gateway_post_start.sh — Runs after every gateway start/restart |
| ai.openclaw.cron-state | Every 15 min | update_cron_state.sh |  |
| ai.openclaw.duty-roster-watch | WatchPaths (file change) | duty_roster_watch.sh | Duty Roster WatchPaths trigger — runs fully standalone (zero AI tokens) |
| ai.openclaw.email-check | Every 5 min | check_email.sh | Email checker — uses Mail.app via osascript (no himalaya dependency) |
| ai.openclaw.gateway | Always running | 18789 |  |
| ai.openclaw.heliefb-sync | 2x daily (calendar) | heliefb_cron.sh | HeliEFB Document Sync — cron wrapper |
| ai.openclaw.icloud-watchdog | Every 30 min | icloud_sync_watchdog.sh | icloud_sync_watchdog.sh — Detects stuck iCloud uploads and restarts cloudd |
| ai.openclaw.ops-plan-watch | Every 5 min | ops_plan_watch.sh | Ops Plan Email Watcher — polls Mail.app every 5 min |
| ai.openclaw.will-email-watch | Every 2 min | will_email_watcher.sh | will_email_watcher.sh — Watches for new emails FROM Will in Mail.app |
| com.openclaw.mission-sync | WatchPaths (file change) | watch_missions.sh | Watch Obsidian vault Missions folder for changes, sync to Google Sheet |
| com.openclaw.wa-watchdog | Always running | wa_watchdog.sh | WhatsApp Watchdog — monitors for disconnections and auto-restarts |
| com.openclaw.wiz-menubar | Always running | wiz_menubar.py | Ensure rumps is available |
| com.thc.fleetmap.hourly | Hourly 7:00–21:00 | fleetpush.sh | **PAUSED** — replaced by fleet-map-watcher (2026-04-04) |
| ai.openclaw.fleet-map-watcher | Always-on (KeepAlive) | fleet-map-watcher.sh | Watches vault Helicopters/Missions/Pilots for .md changes → 5 min debounce → generate.py → git push (zero AI tokens). Uses kqueue_monitor for iCloud. |

## Scripts (`~/.openclaw/workspace/scripts/`)

| Script | Purpose |
|--------|---------|
| add_library_books.py |  |
| alpaca_config.sh | Alpaca Paper Trading Config |
| alpaca_trade.sh | Alpaca Paper Trading Helper |
| build_proverbs_vault.py |  |
| check_email.sh | Email checker — uses Mail.app via osascript (no himalaya dependency) |
| chrome_allow_prompt.sh | chrome_allow_prompt.sh — Auto-click Chrome's "Allow remote debugging?" prompt |
| create_ncr_doc.py |  |
| duty_roster_watch.sh | Duty Roster WatchPaths trigger — runs fully standalone (zero AI tokens) |
| gateway_post_start.sh | gateway_post_start.sh — Runs after every gateway start/restart |
| generate_readiness_pdf.py | Changelog: |
| generate_readiness_pdf_20260217.py |  |
| generate_readiness_report.py |  |
| generate_skybridge_readiness_v2.py |  |
| heliefb_cron.sh | HeliEFB Document Sync — cron wrapper |
| heliefb_sync.py |  |
| icloud_idle_watch.py | Changelog: |
| icloud_sync_watchdog.sh | icloud_sync_watchdog.sh — Detects stuck iCloud uploads and restarts cloudd |
| library_batch.py |  |
| make_fillable.py | Changelog: |
| moonboard.py |  |
| moonboard_at.py | Changelog: |
| moonboard_bruteforce.py |  |
| moonboard_test.py | Changelog: |
| notify.sh | Persistent macOS notification (stays until dismissed) |
| ops_plan_watch.sh | Ops Plan Email Watcher — polls Mail.app every 5 min |
| parse_duty_roster.py |  |
| ping_alert.sh | Changelog: |
| process_roster_v2.py | Changelog: |
| read_ops_plan_mail.sh | Read the latest email from Mail.app's "Ops Plan Report" folder (THC account) |
| read_reminders.sh | Read Apple Reminders from SQLite (bypasses AppleScript hang with large lists) |
| reformat_sim_lessons.py |  |
| reverse_sync_planner.py |  |
| send_email.sh | send_email.sh — Reliable email sender via Mail.app (pure AppleScript, no keystroke hacks) |
| skill_audit.py | Changelog: |
| sync_obsidian_missions.py |  |
| sync_sheet_to_obsidian.py |  |
| update_automations_registry.sh | Auto-generate memory/automations.md from live cron + launchd data |
| update_duty_dashboard.py |  |
| update_duty_roster_v2.sh | update_duty_roster_v2.sh — Pull fresh roster data from Fleetplan API via Chrome |
| validate_fsr.py |  |
| validate_h125_pilots.py |  |
| wa_watchdog.sh | WhatsApp Watchdog — monitors for disconnections and auto-restarts |
| watch_missions.sh | Watch Obsidian vault Missions folder for changes, sync to Google Sheet |
| watch_planner_trigger.sh | Triggered by launchd when /tmp/openclaw/planner-sync-trigger.json changes. |
| will_email_watcher.sh | will_email_watcher.sh — Watches for new emails FROM Will in Mail.app |
| wiz_light.sh | WiZ Light Control - 192.168.100.7 |
| wiz_menubar.py |  |

---

## Heartbeat Checks (HEARTBEAT.md)

- Apple Reminders (THC + Personal lists) — alert if due/overdue
- WhatsApp health — check gateway logs for errors
- Agent health — check cron job states for consecutive errors

## SFLA Report Skill (`skills/sfla-report/`)

Zero AI tokens. One command does screenshot + PDF:
```bash
bash ~/.openclaw/workspace/skills/sfla-report/scripts/run_report.sh [year month]
# Examples:
bash ~/.openclaw/workspace/skills/sfla-report/scripts/run_report.sh          # previous month (auto)
bash ~/.openclaw/workspace/skills/sfla-report/scripts/run_report.sh 2026 5    # May 2026
bash ~/.openclaw/workspace/skills/sfla-report/scripts/run_report.sh current  # this month
```
Output: `~/Desktop/Willy/SFLA_Report_YYYY-MM.pdf` + OneDrive `Missions/Riyadh UAM/SFLA Monthly Reports/`

**Monthly reminders added 2026-04-09:** Apple Reminders → Short term list → SFLA Report — May/Oct 2026. Will runs bash command himself, sends to POI, marks done.
