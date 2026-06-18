# mysterwolf studios — Skill Library
**Last updated:** June 2026
**Total skills:** 14
**Default mobile framework: Flutter. React Native is legacy (Attenuate, Mission Control only).**

A collection of Claude Code skills for the mysterwolf studios app and consulting portfolio.
Reference this file at the start of any session to know what skills are available.

---

## How to Use Skills

**Start a dev session:**
```
load-context [repo nickname]
```

**Scaffold something new:**
```
spinup-app-flutter   (new Flutter app — DEFAULT)
spinup-app-rn        (new React Native app — LEGACY, existing projects only)
spinup-site          (new website)
spinup-profile       (operator demo profile for CannaGuide/StashPass)
```

**Edit existing code:**
```
edit-component
```

**End of session:**
```
update-context
sync-skills    (if new skills were downloaded or created)
session-sync   (update project summary and matrix — run in main Claude chat)
```

---

## Available Skills

### 🏗️ Build Skills

| Skill | Triggers | What it does |
|-------|----------|-------------|
| `spinup-site` | "build a site", "create a website", "spin up a landing page" | Scaffolds a React/Vite site. Pattern A (editorial minimal) or Pattern B (gallery/portfolio). CSS variables, JSON data files, GitHub Pages deployment. Enhanced components: animated stats, marquee, noise texture, lightbox. |
| `spinup-app-flutter` | "create a new app", "spin up an app", "scaffold a new app", "build a new mobile app" | **DEFAULT.** Scaffolds a Flutter app. Flutter stable, Dart, Provider, go_router, SharedPreferences. MWS splash in Flutter, ThemeData with MWS tokens. Optional: BLE, GPS, notifications, Claude API, RevenueCat IAP, SQLite. Reference: DPad Pilot. Generates CLAUDE.md. |
| `spinup-app-rn` | "scaffold a React Native app", "spin up an Expo app" | **LEGACY — existing RN projects only.** Scaffolds a React Native app. Expo bare workflow, Android-first. ThemeContext, MWS splash, navigation, AsyncStorage. Optional: BLE, GPS, Claude API chat, RevenueCat IAP, SQLite. Generates CLAUDE.md. |
| `ship-build` | "ship the build", "release", "push and deploy" | Commits pending changes, builds the release APK, installs on all connected devices (USB + wireless ADB), pushes to GitHub, overwrites the permanent `latest` release with a fixed-name APK asset so the download URL never changes. Updates CLAUDE.md changelog. |
| `spinup-profile` | "build a profile for", "create a store mockup", "make a demo for [store name]" | Generates a personalized operator profile mockup for CannaGuide/StashPass. Searches for real business data, applies category-specific color scheme, produces a demo-ready React component with functional links. Cannabis, coffee, barbershop, boutique palettes included. |

### ✏️ Edit Skills

| Skill | Triggers | What it does |
|-------|----------|-------------|
| `edit-component` | "edit this component", "fix this bug", "add this feature", "update this screen" | Safely edits existing app features. Flutter default. Flutter apps: CannaGuide, DPad Pilot, DPad Flame, Meez, Spoke. RN legacy: Attenuate, Mission Control. Context first, invariants respected, test before commit, CLAUDE.md updated after. |
| `update-portfolio` | "add [app] to the portfolio", "update the portfolio", "add this to mysterwolf.studio", "list [app] on the site", "update [app] status" | Adds or updates an app entry on mysterwolf.studio. Handles apps.json schema, STATUS_MAP registration for new statuses, deploy, and source commit. Includes full field reference and ordering rules. |

### 🔍 Context Skills

| Skill | Triggers | What it does |
|-------|----------|-------------|
| `load-context` | "load-context", "get up to speed", "orient yourself", "read the context file" | Reads CLAUDE.md at session start. Confirms all invariants. Lists pending work in priority order. Waits for instructions — makes no changes until asked. |
| `update-context` | "update the context", "update CLAUDE.md", "document what we did", "save the session" | Writes or updates CLAUDE.md after a dev session. Standard format across all repos. Commits and pushes. |
| `audit-repo` | "audit the repo", "what's in the repo", "show me the structure", "what's deployed" | Read-only repo snapshot. Standardized markdown report. Flags orphaned assets, broken references, missing CLAUDE.md, deployment config issues. |

### 📋 Project Skills

| Skill | Triggers | What it does |
|-------|----------|-------------|
| `session-sync` | "update the summary", "update the matrix", "sync the project", "document what we did" | Run in main Claude chat (not Claude Code). Generates dated matrix entries for Unified Thread Matrix - Claude + updates ProjectConversationSummary .docx. Two outputs always. |
| `sync-skills` | "sync skills", "update the skills repo", "push new skills", "I downloaded new skills" | Syncs local .skill files to this repo. Updates this README manifest. Never deletes existing skills. |
| `sync-mas` | "sync inventory", "sync the sheet", "run the MAS sync", "pull new form submissions" | Fetches the Mobile Art Services Google Form response sheet (Formatted tab), maps rows to inventory CSV schema, translates French captions via Claude API, generates QR codes, appends new staged entries to public/data/inventory.csv. Runs fully without API key — flags French text for manual review if key absent. |

---

## Repo Index

| Repo | Type | Nickname | CLAUDE.md |
|------|------|----------|-----------|
| MysterWolf/dpad_pilot | Flutter/Android | `dpad` | ✓ |
| MysterWolf/dpad_flame | Flutter/Android | `dpad-flame` | ✓ |
| MysterWolf/CannaGuide | Flutter/Android | `cannaguide` | ✓ |
| MysterWolf/attenuate | React Native (legacy) | `attenuate` | ✓ |
| MysterWolf/ebike-app | React Native (legacy) | `mission-control` | ✓ |
| MysterWolf/stashpass-api | Fastify/TS API | `stashpass-api` | ✓ |
| MysterWolf/mobile-art-services | React/Vite site | `mas` | ✓ |
| MysterWolf/studios | React/Vite site | `mysterwolf` | ✓ |
| MysterWolf/processmind | React/Vite site | `processmind` | ✓ |
| MysterWolf/processmind-audit | React/Vite tool | `processmind-audit` | ✓ |
| MysterWolf/skills | Skills library | `skills` | this file |

---

## Session Patterns

### Standard dev session
```
load-context [nickname]     ← orient
[task]                       ← work
update-context               ← document
```

### New project
```
spinup-app-flutter           ← Flutter (DEFAULT)
spinup-app-rn                ← React Native (legacy projects only)
spinup-site                  ← website
```

### Audit before changes
```
audit-repo                   ← understand current state
load-context [nickname]      ← load invariants
[task]                       ← work safely
```

### Recovery after account reset or new session
```
1. Open this README — know what skills exist
2. load-context [nickname] in Claude Code
3. Paste latest ProjectConversationSummary_YYYY-MM-DD.docx into main Claude chat
4. Start from the Where We Left Off table
```

---

## MWS Brand Reference (Quick Access)

**MWS mark:** Circle badge, Georgia serif "mws", double gold ring
- Light: bg `#FDFCFA` · text `#111009` · ring `#C4A962`
- Dark: bg `#0E0D18` · text `#FDFCFA` · ring `#C4A962`
- Sizes: 120px (splash) · 36px (nav) · 24px (footer)

**Brand palette (mysterwolf.studio):**
```
background: #F7F6F3  surface: #EFEEE9  accent: #C4A962  ink: #111009
```

**Mission Control theme tokens:**
```
Day:   bg #F1F3F5  accent #FF5A00  telemetry #00B464
Night: bg #1A1D1A  accent #FF5A00  warning #D9381E
```

**ProcessMind LLC:**
```
bg #0A0C12  gold #C4A962  text #E8E6E0
```

---

*mysterwolf studios · Building tools for the spaces big software ignores.*
