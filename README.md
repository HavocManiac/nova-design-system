# nova-design-system (draft)

**Purpose:** sanitized mirror of the §25 Nova Design System, safe to link into Claude Design (`claude.ai/design`) or share with partner teams. Contains ONLY the design-system surface from Playbook §25 — no agent-side code, no secrets, no customer data, no brand IP beyond what §25 already specifies.

**Status:** DRAFT. Built 2026-04-21 as part of epic `4F-ClaudeDesignBridge` (ADR-057). Not yet pushed to a GitHub repo — Chris pushes when ready, then links the repo in Claude Design as the design-system source.

## What's in here

```
nova-design-system-draft/
├── README.md                       (this file)
├── tokens/
│   ├── colors.css                  (Playbook §25.1 CSS variables)
│   └── typography.css              (Playbook §25.2 font specs + sizes)
├── css/
│   ├── liquid-glass.css            (Playbook §25.3 mandatory effect)
│   ├── layout.css                  (Playbook §25.4 patterns)
│   ├── interactive.css             (Playbook §25.5 buttons, status, transitions)
│   ├── backgrounds.css             (Playbook §25.6 hero + data page treatments)
│   ├── data-viz.css                (Playbook §25.7 charts, stat cards, tables)
│   ├── animations.css              (Playbook §25.8 marquee, fade, pulse, orb)
│   └── patterns.css                (Playbook §25.11 dashboard component patterns)
└── skeletons/
    ├── dashboard-page.html         (generic Nova dashboard page shell)
    ├── hero-page.html              (hero-style landing page shell)
    └── stat-card-grid.html         (stat-box pattern §25.11.1)
```

## What is NOT in here (safety)

- No `agent_config` dumps, no secrets, no WAF keys
- No Telegram bot token
- No deploy API keys
- No voice samples (Wildwoods / UNS brand content)
- No `agent_memory` content
- No customer data from Monday.com
- No proprietary business logic

## Before pushing to GitHub

Chris — review each file against the "what is NOT in here" list before `git init` + `git push`. If anything from that list has crept in, strip it first. Intended repo name: `nova-design-system` (public OK since it contains only the spec Claude Design will consume).

## Phase 0 pilot usage

1. **One-command setup** (assuming `gh` CLI is installed and authenticated):
   ```bash
   cd /Users/main/Documents/Claude/Projects/Nova/nova-design-system-draft
   ./SETUP.sh
   ```
   This initializes git, creates the `nova-design-system` repo on GitHub, and pushes. Output includes the repo URL to paste into Claude Design.

2. **Link the repo** in Claude Design's design-system settings at [claude.ai/design](https://claude.ai/design).

3. **Run the three Phase 0 pilots in recommended order:**
   - (1) Wildwoods rebuild — cleanest first pilot
   - (2) UNS proposal deck template — revenue-adjacent win
   - (3) Dashboard mobile pass (Overview module) — round-trip fidelity test

4. **Exports land in `../design-intake/`** with filename `{target}__{bundle_sha7}.zip`, plus a matching `eval-logs/{sha7}.md` note.

## Phase 1 transition

When 4F-CD.2 (schema + POST /design/ingest) lands, update this repo's README to note that Phase 1 accepts upload flow via the ingest endpoint; this repo continues to serve as Claude Design's design-system source.

## Spec source

Primary source of truth: Playbook §25 "NOVA DESIGN SYSTEM" (added 2026-03-31, current v4.27.0). Pull fresh via `GET /api/agent/sections/query?domain=dashboard`. If §25 diverges from these files, §25 wins — re-sync this repo.
