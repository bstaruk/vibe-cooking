# Seasoning log

Every change to how we work (rules, formats, skills, persona) gets an entry here, newest first. Git holds the diffs. This file holds the reasons. Written by `/season`.

## 2026-09-13: Kitchen tickets & ground rules

- **Branches & PRs:** all work happens on a branch and reaches `main` through a pull request that Brian merges. Branch protection enforces this.
- **Commit locally anytime; push only when asked:** Claude commits locally whenever a unit of work is done. Claude never pushes or touches pull requests unless Brian explicitly asks, and doesn't bring it up otherwise. This rule was added after Claude opened the first PR without being asked. `settings.json` now requires permission for every push and PR command.
- **Kitchen tickets:** commit messages nod to Conventional Commits with three prefixes: `feast:` (new), `season:` (learned or adjusted), and `chop:` (prep work). The first draft had nine types plus scopes. Brian cut it down, because structure only helps if nobody has to think about it (see `.claude/rules/kitchen-tickets.md`).
- **Public by design:** the repo is public on purpose, to show AI collaboration beyond code. Guardrails keep out secrets, exact locations, other people's details, photo GPS data, paywalled content, and affiliate links (see `CLAUDE.md`).
- **Replaces** the first layer's "commit to `main`" rule.

## 2026-09-13: First layer

- **Set up the notebook.** It has a kitchen inventory, recipes, a journal, techniques, research, and sources, all maintained through skills.
- **Persona.** Patina is a seasoned mentor: calm, science-first, dry wit, with brigade callouts in cook mode. Details and adjustable settings are in `PATINA.md`.
- **House laws** (`CLAUDE.md`, `.claude/rules/`):
  - Grams first; volume appears only as helper text.
  - Every step restates its quantities inline.
  - °F first, with a °C helper.
  - Gear Brian owns is named by its call name.
  - Gear advice always gets fresh web research.
- **The loop.** `/menu → /recipe → /cook → /debrief`, plus `/gear`, `/learn`, and `/kitchen` as side trips, and `/season` to tune the whole thing.
- **Trusted sources.** `SOURCES.md` was seeded from web research checked on 2026-09-13.
- **Git.** Commit automatically to `main` after each unit of work. Never push unless asked (`git push` always prompts).
- **Deliberately left out:** scripts, hooks, and CI. Everything is markdown that both of us can read and edit.
