---
paths:
  - "recipes/**"
---

# Recipe format (house style)

Every file in `recipes/` uses this format. Measurement rules are in `.claude/rules/units.md`. A worked example is in `.claude/skills/recipe/example.md`.

## Principles

1. **Readable top to bottom without scrolling back.** Every step includes its own amounts, gear, temperatures, and cues.
2. **Easy to scan with wet hands.** Bold the amounts in the ingredient list, and the times and temperatures in the method.
3. **Written for our kitchen.** Refer to Brian's gear by its call name, and fold in what we've learned.
4. **Clean and neutral.** The persona belongs in chat, not in the file.

## Frontmatter

~~~yaml
---
title: Cast Iron Skillet Cornbread
status: raw          # raw · seasoned · heirloom · retired
version: 1           # bump when quantities or method change
rating:              # 1–5 from the latest debrief; blank until cooked
serves: 8
yield: one 10" (25cm) round
active: 15 min
total: 50 min
tags: [bread, cast-iron, side]
source: Adapted from <author, work>   # or "Original"
source_url:
created: 2026-09-13
last_cooked:
cooks: 0             # number of logged cooks (journal entries)
---
~~~

**Status ladder**

- `raw`: written but never cooked by us.
- `seasoned`: cooked at least once and still being adjusted.
- `heirloom`: the final house version. Only change it with a good reason.
- `retired`: replaced or abandoned. Keep the file and explain why in the *Changelog*.

## Section order

Leave out an optional section if there's nothing to put in it. Never change the order.

~~~markdown
# Title

> One-sentence hook: what it is and what makes this version ours.

![Descriptive alt text](../journal/2026/photos/….jpg)   (optional hero: the best journal photo, linked not copied)

**Serves** 8 · **Active** 15 min · **Total** 50 min · **Status** raw · v1

## Why this works          (2–4 bullets: the technique and science that matter)
## Equipment               (call names + role)
## Ingredients             (grouped by component when there's more than one)
## Baker's percentages     (bread, dough, pastry only)
## Method                  (### phases → numbered steps)
## Make ahead & storage    (optional)
## Riffs                   (optional; untested ones marked *(untried)*)
## Notes & lessons         (dated bullets from /debrief, linked to journal entries)
## Changelog               (vN (date): what changed and why)
## Sources
~~~

## Equipment lines

- Format: `- **12" Smithey skillet**: sear`. Call names must match `kitchen/equipment.md` exactly.
- If Brian doesn't own the item: `- **Stand mixer**: knead *(not owned; by hand: 10 min slap-and-fold)*`.

## Ingredient lines

Format: `- **amount** ingredient (helper), prep`

- `- **225g** yellow onion (1 medium), ½" (1cm) dice`
- `- **5g** kosher salt (1½ tsp Diamond Crystal)`
- **Divided ingredients:** give the total, then the split in the order the steps use it: `- **70g** unsalted butter (5 tbsp), divided: 15g for the skillet · 55g melted for the batter`
- **Optional ingredients:** add `(optional)` at the end, after the helper.
- **Order:** within each group, list ingredients in the order they're used.

## Method rules

- **Phases** are `###` headings that name what's happening, with lead time when it matters: `### Night before (12–24 h ahead)`, `### Sear`, `### Pan sauce`.
- **Steps** are numbered and start with a bold action label: `3. **Whisk the wet.** …`
- **Always put quantities inline.** Every ingredient in a step appears with the amount used in that step: "Whisk 340g buttermilk and 100g beaten egg". Never write "whisk the wet ingredients" or "add the remaining butter" without the grams.
- **Name the vessel** by its call name the first time it appears in each phase ("the 10" Lodge skillet"). After that, "the skillet" is fine.
- **Bold times and temperatures.** Every time needs a cue: `Bake **20–25 min**, until the top is deep golden and the center reads **200°F (93°C)**.`
- **Parallel work and preheats** go in the step where they need to start: "Start the oven now: **425°F (220°C)**."
- **Safety notes** go inline in the step where they matter: hot handles, splatter, and below-USDA temperatures along with the pasteurization numbers.

## Lint checklist

Run this every time a recipe is created or edited. `/season` also runs it across all recipes.

- [ ] No volume unit (`tsp`, `tbsp`, `cup`, `fl oz`, `ml`) appears outside parentheses, and "teaspoon", "tablespoon", and "cup" are never the main measure.
- [ ] Every ingredient in the list appears in the method with its amount, and the portions of each divided ingredient add up to its total.
- [ ] The method doesn't use anything that's missing from the ingredient list.
- [ ] Every temperature is written `°F (°C)`.
- [ ] Every time has a cue.
- [ ] Every call name exists in `kitchen/equipment.md` (or is marked not owned), and each vessel is big enough.
- [ ] The frontmatter is complete, and the header line matches it (serves, times, status, version).
- [ ] The recipe's row in `recipes/README.md` is up to date.
