---
name: season
description: Tune how we work, one retro at a time. Audits the notebook for drift (recipe format violations, stale indexes, broken links, outdated research), looks for patterns in recent cooks, and proposes changes to house rules, skills, templates, persona, and sources. Use for a periodic retro ("let's do a retro", "season the repo"), after about 5 logged cooks, or when Brian wants to change how we work ("from now on…", "I don't like how you…", "tone down the lingo").
argument-hint: "[focus area or change request]"
allowed-tools: Bash(git log *)
---

# /season: tune the system

Focus: `$ARGUMENTS`

Seasoning builds up one thin, deliberate layer at a time. Each pass should make the system a little more ours. Make small, specific changes, not rewrites.

## Recent history

!`git log -40 --date=short --pretty=format:"%ad  %s"`

## Quick change

Use this path when Brian asks for something specific, like "from now on, bold every timer" or "less brigade lingo."

1. Find where the behavior is defined (`PATINA.md`, `.claude/rules/*`, a skill, or `CLAUDE.md`) and change it there. Each rule lives in exactly one place. Don't copy rules between files.
2. If existing files break the new rule (recipes, for example), offer to update them now.
3. Add an entry to `SEASONING.md` and commit it as `season: <change>`, or as `season!:` if existing files had to be migrated (see `.claude/rules/kitchen-tickets.md`). Skip the full retro.

## Full retro

### 1. Audit the notebook

List what you find, but don't fix anything yet.

- **Recipes:** run the lint checklist from `.claude/rules/recipe-format.md` on every file in `recipes/`. Grep for `tsp|tbsp|cup|teaspoon|tablespoon|fl oz` and check each hit to see whether it's a primary measure. Also look for steps missing inline amounts, `°F` without `(°C)`, and missing frontmatter fields.
- **References:** equipment call names used in recipes that aren't in `kitchen/equipment.md` or have been retired, and broken relative links.
- **Indexes:** `recipes/README.md` and `techniques/README.md` match the files on disk, and each recipe's `cooks` and `last_cooked` match its journal entries.
- **Staleness:** `research/` reports past their `refresh_after` date, `raw` recipes that have sat on deck for months, and wishlist items stuck in "researching."
- **Sources:** entries in `SOURCES.md` older than a year without a status check, sources the journal says misled us, and new names that keep coming up.
- **Git:** local branches that have already been merged and can be deleted.

### 2. Look for patterns

Go through the journal entries since the last `SEASONING.md` entry and look for:

- The same failure showing up 2+ times. Each one needs a technique note, a recipe fix, or a gear-gap note.
- Wins worth making standard practice.
- Facts about the kitchen we learned but haven't written down.
- Gear that gets used constantly vs gear that never comes out.
- Skills that get skipped or worked around. That's a sign the skill is wrong, not Brian.

### 3. Ask Brian

Send one message with 2–4 questions. Did anything feel clunky? Is cook mode too chatty or too terse? Anything annoying about the recipe format? Should any of Patina's settings change (wit, lingo, science depth)? Is there a skill nobody uses, or one Brian wishes existed?

### 4. Propose

Give a numbered list of concrete changes. Tag each with its file and a one-line reason. Group them:

- **Fixes:** drift and rule violations.
- **Tuning:** rules, skills, persona.
- **Ideas:** bigger or structural changes.

A new skill needs a real reason to exist. Prefer improving an existing one.

### 5. Apply and log

- Apply whatever Brian approves. Keep each skill under ~500 lines, and keep every rule in one place only.
- Add an entry at the top of `SEASONING.md`:
  ~~~markdown
  ## YYYY-MM-DD: <short title>
  - What changed (file) and why
  - Audit: N fixes applied
  - Parked: ideas we deferred
  ~~~
- Commit it as `season: <title>` (see `.claude/rules/kitchen-tickets.md`).
