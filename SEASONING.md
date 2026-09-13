# Seasoning log

Every change to how we work (rules, formats, skills, persona) gets an entry here, newest first. Git holds the diffs. This file holds the reasons. Written by `/season`.

## 2026-09-13: One rule, one home

- **Why:** the first audit found that rules copied across files had already drifted apart: two different teaspoon helpers for the same 5g of salt, two rounding rules for small amounts, and two opposite rankings for gear evidence. Copies drift; pointers don't.
- **The principle** (`CLAUDE.md` → *Evolving the system*): each rule's details live in exactly one file. Other files can restate a rule as a one-line headline with a pointer.
- **Salt** (`units.md`, `pantry.md`): the house salt is coarse sea salt. Its crystals vary too much by brand and grind for a generic teaspoon conversion, so salt helpers wait until we weigh a teaspoon. Reference weights for other brands now live only in `units.md`, for converting source recipes.
- **Gear evidence** (`SOURCES.md`): one table matches each kind of question to its best source (specs for dimensions, testing for performance, owner patterns for durability, retailers for price). `/gear` and `kitchen-scout` point to it.
- **Pointers instead of copies:** `/cook` rounding, `/recipe` lint, time cues in `recipe-format.md`, and the README's license and settings notes.
- **Time cues** (`units.md`): rests, holds, and storage times no longer need a cue. Cooking, proofing, and chilling times still do.
- **Mid-cook notes** (`CLAUDE.md`): "write things down right away" now defers to `/cook`, which keeps a running note for `/debrief`.
- **Example recipe:** now passes its own checklist (exact surface-temp conversion, a reheat cue, house salt).
- **Audit:** `/season` now looks for rule details outside their home.

## 2026-09-13: Kitchen tickets & ground rules

- **Branches & PRs:** all work happens on a branch and reaches `main` through a pull request that Brian merges. Branch protection enforces this.
- **Commit locally anytime; push only when asked:** Claude commits locally whenever a unit of work is done. Claude never pushes or touches pull requests unless Brian explicitly asks, and doesn't bring it up otherwise. This rule was added after Claude opened the first PR without being asked. `settings.json` now requires permission for every push and PR command.
- **Kitchen tickets:** commit messages nod to Conventional Commits with three prefixes: `feast:` (new), `season:` (learned or adjusted), and `chop:` (prep work). The first draft had nine types plus scopes. Brian cut it down, because structure only helps if nobody has to think about it (see `.claude/rules/kitchen-tickets.md`).
- **Public by design:** the repo is public on purpose, to show AI collaboration beyond code. Guardrails keep out secrets, exact locations, other people's details, photo GPS data, paywalled content, and affiliate links (see `CLAUDE.md`).
- **License:** MIT for the setup (`.claude/`, `CLAUDE.md`, `PATINA.md`) so anyone can borrow the workflow. CC BY 4.0 for the content (recipes, notes, photos).
- **Photos:** welcome. Each photo is resized to a 1600px JPEG with all metadata, including GPS, stripped by ImageMagick and checked with ExifTool, and the frame is checked for anything that shouldn't be public (`.claude/rules/photos.md`). No scripts; just two Homebrew tools. Originals go in a gitignored `inbox/`.
- **Brian's words:** journal entries quote Brian's reaction verbatim alongside Claude's diagnosis, so readers see the real exchange and not only Claude's summary.
- **Food safety:** the README notes that these are a home cook's notes, and that any recipe going below USDA temperatures says so, with the numbers.
- **Rebase merges:** every commit lands on `main` as written, so each one should be a real ticket. Unpushed mistakes get amended, not patched with another commit.
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
