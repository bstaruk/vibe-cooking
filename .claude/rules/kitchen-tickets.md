# Kitchen tickets: commits, branches & PRs

In a restaurant, every order is a ticket on the rail: short, standardized, and readable at a glance by anyone on the line. Our git history works the same way. The structure comes from Conventional Commits and the vocabulary comes from the kitchen.

## The flow

1. **Never work on `main`.** Before the first file edit of any unit of work, check which branch you're on. If it's `main`, run `git switch main && git pull --ff-only && git switch -c <type>/<slug>`. Branch protection on GitHub enforces this too.
2. **One branch per unit of work.** A unit is a recipe, a debrief, a research report, a kitchen tour, or a retro. A branch can hold several tickets (commits).
3. **Building on unmerged work?** If new work depends on a branch whose PR is still open (like debriefing a recipe that hasn't merged), commit onto that branch and update its PR instead of starting a new one.
4. **Ship it** when the unit is done: commit, `git push -u origin <branch>`, and open a PR with `gh pr create`. If a PR already exists, pushing updates it.
5. **Brian merges.** Only merge when Brian says so ("merge it"). Then run `gh pr merge --squash --delete-branch`, followed by `git switch main && git pull --ff-only`, and delete the local branch.
6. **Never touch git in the middle of a cook.** Ship after the debrief.

## Branch names

Use `<type>/<kebab-slug>`:

- `plate/cast-iron-cornbread`
- `taste/2026-09-20-cornbread`
- `forage/carbon-steel-woks`
- `stock/kitchen-tour`
- `season/retro-2026-10`

## Ticket format

~~~
<type>(<scope>)[!]: <summary>

[body: what changed and why; where the lessons went]

[Behind: <what this changes about how we work, and what was migrated>]
~~~

- **Summary:** lowercase, no trailing period, 72 characters or fewer. An imperative verb or a noun phrase both work, and numbers and units are welcome: `season(recipe): cornbread v2, pull at 21 min`.
- **Scope:** always required. Pick one from the list below.
- **Body:** optional for small tickets. `taste` tickets should list where each lesson was recorded.

## Types

| Type | In the kitchen | Borrowed from | Use for |
|---|---|---|---|
| `plate` | A new dish goes out | `feat` | A new recipe, technique note, menu, skill, or capability |
| `taste` | Tasting notes after service | none | Journal entries and debriefs, including the lessons folded back into recipes and techniques |
| `season` | Adjusting to taste | `refactor` / `perf` | Tuning something that already exists: recipe tweaks and version bumps, rules, skills, persona |
| `rescue` | Saving a broken sauce | `fix` | Correcting a mistake: wrong quantity, bad conversion, broken link, outdated fact |
| `stock` | Restocking the kitchen | none | Updates to equipment, pantry, profile, or wishlist |
| `forage` | Going out for the good stuff | `docs` | Gear research reports and changes to `SOURCES.md` |
| `mise` | Mise en place | `chore` / `build` / `ci` | Repo setup, settings, indexes, housekeeping |
| `garnish` | Finishing touches | `style` | Formatting, typos, and wording that don't change meaning |
| `86` | Off the menu | `revert` | Retiring recipes or gear, deleting files, reverting a ticket |

**Choosing a type:** go by the ticket's main purpose. A debrief that also bumps the recipe to v2 is still `taste`. A retro that tunes three skills is `season`.

## Scopes

`kitchen` · `gear` · `recipe` · `menu` · `journal` · `technique` · `sources` · `rules` · `skills` · `persona` · `repo`

## Behind! (breaking changes)

Cooks shout "Behind!" when they walk past someone carrying something hot. Do the same when a ticket changes how we work in a way that affects existing files or habits, such as switching temperatures to °C first or restructuring the recipe format.

Add `!` after the scope, plus a `Behind:` footer that says what changed and what was migrated:

~~~
season(rules)!: temperatures go °C first

Behind: all 14 recipes migrated to "220°C (425°F)"
~~~

## Examples

~~~
mise(repo): set up the notebook, skills, and house rules
stock(kitchen): add 12" Smithey skillet
forage(gear): compare carbon steel woks for induction
plate(recipe): cast iron skillet cornbread v1
taste(journal): cornbread cook #2, 4/5
season(recipe): cornbread v2, pull at 21 min in the 12"
rescue(recipe): buttermilk total didn't match the method
plate(technique): dry brining
season(persona): wit up to 6
garnish(sources): tidy gear tables
86(kitchen): retire the warped nonstick
~~~

## Pull requests

- **Title:** a single ticket in the format above. Squash merging turns it into the commit message on `main`.
- **Body:** keep it short.
  - **What's cooking:** 1–3 bullets covering what changed and why.
  - **Files:** the notable files touched.
  - **Headline:** for recipes and debriefs, add the version, rating, and key lesson.
