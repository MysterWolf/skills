# mysterwolf studios — Skills Library Context
**Last updated:** 2026-06-12
**Total skills:** 13

## What This Is

The `MysterWolf/skills` repo is the Claude Code skill library for mysterwolf studios.
Each `.skill` file is a ZIP archive containing a `SKILL.md` with step-by-step instructions
that Claude Code loads and executes. Skills are the operating procedures for the studio —
how to scaffold apps, edit components, sync context, and manage the portfolio.

## Current Status

- **Repo:** github.com/MysterWolf/skills (branch: main)
- **Downloads mirror:** `~/Downloads/Skills/` — keep in sync with repo after any changes
- **Total skills:** 13

## Skill Inventory

| Skill | Type | Purpose |
|-------|------|---------|
| `spinup-app-flutter` | Build | **DEFAULT** — scaffold new Flutter app (Provider, go_router, MWS splash, ThemeData) |
| `spinup-app-rn` | Build | LEGACY — scaffold React Native / Expo bare app (existing projects only) |
| `spinup-site` | Build | Scaffold React/Vite site — Pattern A (editorial) or Pattern B (gallery) |
| `spinup-profile` | Build | Generate operator demo profile for CannaGuide/StashPass |
| `edit-component` | Edit | Safely edit existing app screens/components — Flutter default, RN legacy supported |
| `update-portfolio` | Edit | Add/update app entry on mysterwolf.studio |
| `load-context` | Context | Read CLAUDE.md, confirm invariants, orient session |
| `update-context` | Context | Write/update CLAUDE.md after a session, commit and push |
| `audit-repo` | Context | Read-only repo snapshot — flags orphans, missing docs, broken refs |
| `session-sync` | Project | Run in main Claude chat — generates Unified Thread Matrix entry + Summary .docx |
| `sync-skills` | Project | Sync `~/Downloads/Skills/` → repo, update README manifest |
| `sync-mas` | Project | Sync Mobile Art Services inventory from Google Form sheet |
| `mysterwolf-site-builder` | Project | Build/update mysterwolf.studio pages and apps.json |

## Architecture Decisions

- Skills are ZIP archives (`.skill` extension) containing a single `SKILL.md` — binary files, never edit in place
- Inner folder name inside the ZIP must match the skill name (e.g. `spinup-app-flutter/SKILL.md`)
- README.md is the human-facing index; CLAUDE.md (this file) is the Claude Code session context
- Downloads mirror (`~/Downloads/Skills/`) must be kept in sync with the repo after any changes — copy repo → Downloads after edits, not the reverse

## Invariants — Never Change These

- **spinup-app-flutter is the default for all new MWS mobile apps.** Never direct new projects to spinup-app-rn.
- **spinup-app-rn is legacy only** — Attenuate and Mission Control. Do not use for new projects.
- **Flutter apps: CannaGuide, DPad Pilot, DPad Flame, Meez, Spoke.**
- **React Native legacy apps: Attenuate, Mission Control.**
- **Inner ZIP folder must match skill name** — mismatched names cause skill load failures.
- **Never delete skills without explicit instruction** — deprecate by renaming to `[name].skill.deprecated`.
- **After any skill edit:** rebuild the ZIP from the modified SKILL.md, copy to Downloads mirror, commit and push.

## How to Edit a Skill

```bash
# 1. Unpack
mkdir /tmp/skill_edit && cp ~/skills/[name].skill /tmp/skill_edit/
cd /tmp/skill_edit && unzip [name].skill -d extracted

# 2. Edit
# Edit extracted/[name]/SKILL.md

# 3. Repack (inner folder name must match skill name)
cd extracted && zip -r ../{name}.skill [name]/

# 4. Copy to repo and Downloads
cp /tmp/skill_edit/[name].skill ~/skills/
cp /tmp/skill_edit/[name].skill ~/Downloads/Skills/

# 5. Commit
cd ~/skills && git add [name].skill README.md CLAUDE.md
git commit -m "feat: update [name] skill — [summary]"
git push origin main
```

## Pending Work

- `spinup-site` — review for staleness; confirm Pattern A/B still match current mysterwolf.studio output
- `session-sync` — confirm Unified Thread Matrix format still matches active .docx template
- `edit-component` — body still has heavy RN focus in common patterns section; update Flutter patterns

## Claude Code Session Starter

Load this repo with `load-context skills`. The README is the human index; this CLAUDE.md is
the session context. When asked to edit a skill, always unpack the ZIP, edit SKILL.md, repack
with the correct inner folder name, copy to both the repo and `~/Downloads/Skills/`, then commit.
Never hardcode skill content — always work from the unpacked SKILL.md.

## Changelog

### 2026-06-12 — Flutter default, spinup-app renamed, edit-component and README updated
- `spinup-app-flutter` created — default for all new MWS mobile apps; Flutter stable, Provider,
  go_router, SharedPreferences, MWS splash in Dart, ThemeData MWS tokens, optional BLE/GPS/
  notifications/Claude API/RevenueCat/SQLite; reference DPad Pilot
- `spinup-app` renamed to `spinup-app-rn` — LEGACY banner added, description updated
- `edit-component` — description updated: Flutter default declared; App Quick Reference table
  updated with framework (Flutter vs RN legacy) and status columns
- `README.md` — total 13, default mobile framework note, repo index expanded (CannaGuide,
  Attenuate, stashpass-api), build table and session patterns updated
- `CLAUDE.md` created (this file)
- `~/Downloads/Skills/` — brought in sync: spinup-app.skill removed, three updated files added
