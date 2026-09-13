# Seasoning log

Every change to how we work (rules, formats, skills, persona) gets an entry here, newest first. Git holds the diffs. This file holds the reasons. Written by `/season`.

## 2026-09-13: Kitchen tickets

- **Why:** Brian wants every change to go through a pull request (with branch protection on `main`), and a commit style with some personality.
- **Branches & PRs:** all work happens on `<type>/<slug>` branches and ships as a PR, and Brian merges. Pushing branches is now routine; force-pushes still ask first.
- **Kitchen tickets:** a culinary twist on Conventional Commits, `<type>(<scope>)[!]: <summary>`. The types are `plate` · `taste` · `season` · `rescue` · `stock` · `forage` · `mise` · `garnish` · `86`, and breaking changes get a `Behind:` footer (see `.claude/rules/kitchen-tickets.md`).
- **Public repo:** personal details in `kitchen/profile.md` stay general.
- **Replaces** the first layer's rule of "commit to `main`, never push."

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
