# MEMORY.md - Po's Long-Term Memory

## Key Facts
- Will is Chief Pilot at THC (The Helicopter Company), Saudi Arabia
- I'm Po, his copilot assistant. Started: 2026-02-04
- **Renee** — Will's wife (phone: +15417404394)
- **Po's WhatsApp:** +966503091733 (own SIM, linked 2026-03-11)
- **Will's WhatsApp:** +966559703189
- Will homeschools boys aged 6-7

## Will's Quotes & Proverbs
Collected in [[quotes]] — growing list of wisdom and scripture Will shares.

## Preferences
- **WhatsApp reply prefix:** 🦞 + blank line, then message
- Minimal input from Will — automate everything possible
- Anticipate needs, suggest ideas proactively
- **Amazon:** Use amazon.sa

## WhatsApp Groups

| Group | JID | Persona | Notes |
|-------|-----|---------|-------|
| **Mani** | `120363424655374740@g.us` | 📖 Mani (NOT Po) | Read [[mani/SKILL]] + [[mani/INDEX]]. Answer everyone, read-only, no MEMORY.md loading |
| **Recipes** | `120363425655741121@g.us` | Cheeky Po | Auto-generate + print recipe cards on any recipe link. Roast recipes missing meat. |
| **Family Doctor** | `120363425975382824@g.us` | Po (health assistant) | Family health group (Will + Renee). Store health info → `family-health/` workspace folder. Track health reminders. Share insights on demand. |

## Agent Delegation
- **Noti** — Obsidian vault specialist. Delegate ALL vault edits. Trigger: `:obsidian` or `noti`
- **Mani** — THC manuals expert. Read-only + can draft docs to Clawdrop. Trigger: `mani` / `manny`. Auto-reindex via HeliEFB trigger file. Config: [[mani/SKILL]]
- **Renti** — Rental properties. Trigger: `:rental`, `renti`, `tenant`, `talbot`, `bellevue`, `boone`, `monroe`, `cash flow`. Details: [[memory/rental-dashboard]]
- **Workflow:** Spawn Noti for vault changes → wait → run `generate.py` + push fleet map myself.

## Obsidian Conventions
- Add `last_updated: YYYY-MM-DDTHH:MM+03:00` to YAML frontmatter on edits
- Missions folder note: `Missions/Missions.md` (not top-level)

## Active Projects
All ✅ LIVE unless noted. Details in `memory/*.md` files where indicated.

| Project | Live URL | Reference |
|---------|----------|-----------|
| **Fleet Map v2** | [GitHub Pages](https://willslawrence.github.io/thc-fleet-map-v2/) | [[memory/fleet-map]] |
| **SFLA Trackers** (Riyadh UAM + KAFD-Malham) | [Riyadh](https://willslawrence.github.io/sfla-tracker/) / [Malham](https://willslawrence.github.io/sfla-malham-tracker/) | [[memory/sfla]] |
| **Duty Roster V2** (Fleetplan API) | [GitHub Pages](https://willslawrence.github.io/thc-duty-roster-v2/) | [[memory/duty-roster]] |
| **Pilot Planner V2** | [GitHub Pages](https://willslawrence.github.io/pilot-planner/) | [[memory/pilot-planner]] |
| **Read for Rewards** | [GitHub Pages](https://willslawrence.github.io/read-for-rewards/) | [[memory/read-for-rewards]] |
| **Friends Library** | [GitHub Pages](https://willslawrence.github.io/friends-library/) | [[memory/friends-library]] |
| **Giving Dashboard** | [GitHub Pages](https://willslawrence.github.io/giving-dashboard/) | [[memory/giving-dashboard]] |
| **Giving Vote** | [GitHub Pages](https://willslawrence.github.io/giving-vote/) | [[memory/giving-vote]] |
| **Vehicle Maintenance** | [GitHub Pages](https://willslawrence.github.io/vehicle-maintenance/) | [[memory/vehicle-maintenance]] |
| **[[Rental Dashboard]]** | [GitHub Pages](https://willslawrence.github.io/rental-dashboard/) | [[memory/rental-dashboard]], agent: `renti` |
| **CCR Church App** | [GitHub Pages](https://willslawrence.github.io/ccr-app/) | [[memory/ccr-app]], [[memory/ccr-app-todo]] |
| **New Port Hill** (Ben Ritter) | [v3](https://willslawrence.github.io/new-port-hill-analysis/v3.html) | [[memory/new-port-hill]] |
| **Charity Audit** | — | Skill: [[skills/charity-audit/SKILL]] |
| **Recipe Cards** | — | [[memory/recipe-cards]] |
| **Ops Plan Pipeline** | — | [[memory/ops-plan-pipeline]] |

- **Sim Program KPIs** — See [[memory/kpis]].
- **KMZ/KML Styling** — Featured Classes master KMZ (22 styles). Style guide at [[KMZ_STYLE_GUIDE]]. Green for Third/Truck lines. Watch `kml:` prefix (breaks Garmin Pilot).
- **Fleetplan Data Extraction** — See [[memory/fleetplan]] and [[skills/fleetplan/SKILL]]. `window.bryntum` is DEAD — API approach only.
- **OPS Report Auto-Sync** — See [[memory/ops-plan-pipeline]]. Replace flights, don't append. FSR validation mandatory.
- **HeliEFB Doc Sync** — Mon & Thu 6AM. See [[memory/heliefb]].
- **Apple Reminders** — Source of truth for TODOs. Default list: "Short Term".

## Infrastructure
- **Tailscale:** Mac Pro `100.87.229.68` (`po-pro`) | Mac Air `100.96.45.50` | iPhone `100.76.234.77`. Key expiry disabled on all. Auto-update OFF. Auth key in `~/.openclaw/.env.tailscale` (stored in Obsidian vault `Tailscale.md`, expires ~July 2026 — rotation reminder set). Details: [[memory/tailscale]]
- **Remote Access:** SSH (`ssh pro` from Air) + Screen Sharing over Tailscale. Details: [[memory/remote-access]]
- **OpenClaw Control UI:** Accessible from Mac Air via Tailscale (paired 2026-03-19)
- **Chrome Attach:** `profile="user"` for Will's logged-in Chrome. Details: [[memory/chrome-attach]]
- **QMD:** v1.0.6 local vector search. Collections: memory-dir, memory-root, ops/trading/admin/security-memory.
- **Model:** Primary `minimax/MiniMax-M2.7` (system default). #opus → Opus only. All other channels use MiniMax-M2.7.
- **OpenClaw:** 2026.4.2 (updated 2026-04-04)
- **Background automation cost:** ~$45-55/mo (crons + heartbeats). Zero-AI launchd scripts save ~$30-35/mo.
- **Discord:** Server `1489709290318204928`, bot active. Channel map in AGENTS.md.
- **Gateway bind:** Loopback only (changed 2026-04-03). Control UI local-only.
- **File sharing: Taildrop** (replaced Clawdrop 2026-04-03). Direct device-to-device via Tailscale. Auto-receive watcher on Pro (`com.po.taildrop-watcher`) saves to `~/Downloads/Taildrop/`. Send via `tailscale file cp <file> <device>:`
- **Fleet Map Watcher:** `ai.openclaw.fleet-map-watcher` — fswatch/kqueue_monitor on vault Helicopters/Missions/Pilots. 5min debounce, runs generate.py + git push. Zero AI tokens. Replaced hourly cron.
- **Tailscale IP (Pro):** `100.87.229.68` / hostname `po-pro.tailc292b0.ts.net` (changed from 100.116.53.23 on 2026-04-14 — Tailscale re-created node)
- **Tailscale node change runbook:** [[memory/knowledge/systems/tailscale-node-change-runbook]]
- **Brave Search:** Configured in openclaw.json

## Sim Program Key Facts
- 13 line pilots (exclude management: Will, Matthias Klemp, Gilles Plaisance, Roberto Piani)
- Target: 15 lessons/pilot/year (2 per rotation)
- KPI weights: Sim 30% + Check Pilot 25% + AAM 10% + UAM 25% + Rally 10%

## Security Rules
- Passphrase required before opening any channel to wide/open access
- Never weaken security without explicit permission + passphrase verification
- Keychain commands BANNED (see AGENTS.md denylist)
- `gog` CLI only for Google APIs — never extract OAuth tokens
- API keys in `.env` files only, never in source

## Key Rules
- **Format stability:** Don't change data formats unless Will explicitly requests
- **H125 regs:** HZHC52-HZHC70 or HZTH50-HZTH70 = H125. Everything else is NOT.
- **Ops plan = replace, not append.** WIPE flights in date range before writing.

## Workflow Patterns (from Peter Steinberger, 2026-04-10)
See [[memory/knowledge/openclauw-tips-peter-steinberger]] for full source.

### Parallel Agents
Spawn multiple sub-agents simultaneously for independent tasks. Like a dev team all working at once.

**Safe to parallelize:**
- Tasks touching different repos (fleet map + CCR app + duty roster)
- Tasks with no shared state or dependencies
- Multiple project health checks at once

**Not safe:**
- Tasks writing to the same file
- Sequential workflow steps
- Anything with dependency order

**Implementation:** AGENTS.md has the behavioral rules. HEARTBEAT.md applies these checks.

### Close the Loop — Verify After Every Action
After any task, explicitly state:
1. **Objective** — what the task was trying to accomplish
2. **Confirmation** — that it was completed correctly
3. **Unexpected** — anything that didn't go as planned

❌ "Done" ← no verification
✅ "Fixed the math error in cell B4. Confirmed: B4 now shows 142, other cells unchanged."

For automated scripts: git status, file timestamps, output errors.
For human tasks: state what was intended, confirm what happened.

**Verification per system:**
| System | What to verify |
|--------|---------------|
| Git push | `git status` clean |
| Fleet map generate | `index.html` timestamp updated |
| Vault write | file exists + content correct |
| Email sent | no error in output; check Sent folder after delay |
| Ops plan parse | flights appear in correct date range |

## Model Performance Observations
- **MiniMax-M2.7:** Reliable, cost-effective. Used for everything unless a channel has an explicit override.
- **Claude Sonnet/Opus:** Reliable for complex reasoning — use only for channels with explicit override.

## Lessons Learned
- **File delivery:** When Will asks for a file, SEND it directly (WhatsApp attachment), or give a link, or put it in Clawdrop and tell him. Don't just tell him the path — he doesn't know where repos live. Open Clawdrop folder so iCloud syncs immediately.
- **NEVER `launchctl bootout/unload` on gateway** — kills Po permanently. Use `gateway restart` or `launchctl kickstart -k`.
- Obsidian vault path: `com~apple~CloudDocs` (iCloud Drive), NOT `iCloud~md~obsidian`
- `GOG_KEYRING_BACKEND=keychain` required for all gog commands
- Email accounts: work `wlawrence@helicopter.com.sa` | Po `cptpolawrence@icloud.com` | backup `cptwilllawrence@gmail.com`
- OneDrive: `/Users/willy/Library/CloudStorage/OneDrive-TheHelicopterCompany/H125 Pilots - Documents/`
- Launchd agents (duty-roster-watch, ops-plan-watch, email-check) are autonomous — don't duplicate their work
- Gateway launchd service: `ai.openclaw.gateway`
- **Email sending:** USE `scripts/send_email.sh` — NEVER inline osascript. Pure AppleScript (no keystrokes — those fail when screen locked).
- **Don't recreate — UPDATE.** Check existing work before rebuilding.
- **Don't repeat yourself.** If you catch yourself re-explaining something you just said, switch to a simple "Done" or "Got it" and stop. Will will ask if he needs more.
- YAML: `Helicopter: H125` (string), NOT list format.
- Chrome: NEVER launch with `--remote-debugging-port` (resets toggle). Fallback: AppleScript `execute javascript`.
- Health data CSV — trust Will's corrected numbers over automated export.
- **Tailscale node recreation** — caused by auto-update (`Apply: true`). Auto-update now disabled. Follow [[memory/knowledge/systems/tailscale-node-change-runbook]]. NEVER expose auth tokens in chat.
- **Control UI device auth** — permanently disabled (`dangerouslyDisableDeviceAuth: true`). Doesn't survive gateway restarts. Token auth is sufficient.
- **Anthropic 529 overloads** — can last all day. OpenAI GPT-4.1 now available as fallback.
- **Anthropic billing:** Max/Pro subscriptions DON'T cover API/third-party tool usage (announced 2026-04-04). API is always per-token. Will on Max plan ($200/mo) — separate from API charges. One-time $200 credit available (redeem by Apr 17).
- **WhatsApp 499 cycling:** Recurring issue (Apr 3-5+). Connects, drops after ~60s, creds.json restored from backup each cycle. Upstream WhatsApp Web instability — no fix on our side. Messages still get through between cycles.
- **CCR App auth:** Username whitelist system (v2.7.0+). Will's account = "lwill". Approved members in `approvedMembers` Firestore collection.
- **Sub-agents + Firebase:** ALWAYS verify API calls against current SDK docs. Don't trust generated Firebase code.
- **CCR App versioning:** 4 files need version bumps (index.html ?v=, app.js APP_VERSION, sw.js APP_VERSION + CACHE_NAME). Miss one → stale cache.
- **Pilot Planner:** Google Sheet = source of truth for rotations, NOT Fleetplan. Admin mode = triple-click version number.
