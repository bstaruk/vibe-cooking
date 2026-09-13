---
name: recipe
description: Write, import, adapt, or scale recipes into the house format. That means grams first, °F (°C), quantities restated inline in every step, and Brian's own gear named by call name. Use when Brian wants to save or create a recipe; turn a URL, cookbook photo, video, or rough notes into a house recipe; adapt or remix an existing one; or convert a volume-based recipe to weights.
argument-hint: "[dish idea | URL | recipe name]"
---

# /recipe: write it the house way

Input: `$ARGUMENTS`

**Read both rule files before writing:** `.claude/rules/recipe-format.md` (format) and `.claude/rules/units.md` (measurements). The worked example is [example.md](example.md). Match its structure.

## 1. Understand the request

- **New recipe from an idea** ("let's do birria"): research it first (step 2).
- **Import** (URL, pasted text, cookbook photo, video transcript): fetch or read the source, then convert it.
- **Adapt an existing house recipe:** edit it in place and bump `version`. If the change is big, add it under *Riffs* or create a new file that links back to the original.
- **Scale or convert only:** for a one-off cook, do it in chat without touching the file (that's `/cook`'s job). For a permanent change, bump the version.

Before writing, check `recipes/README.md` and grep `recipes/` for duplicates or near-duplicates.

## 2. Research (new recipes)

- Compare 2–3 versions from the top tiers of `SOURCES.md`, favoring the go-to experts for that cuisine or technique. Where they disagree, choose on purpose and explain the choice under *Why this works*.
- Check `techniques/` and `journal/` for lessons we've already learned (our oven runs hot, Brian likes more salt). These override generic advice.
- Check `kitchen/profile.md` for diet, tastes, and household size, and set `serves` to fit.

## 3. Convert

- **Volume to grams:** use trusted density data (King Arthur's ingredient weight chart for baking staples, manufacturer or USDA data for everything else). If a conversion is uncertain (packed herbs, chopped vegetables), mark it with `~` and add a line to *Notes & lessons* asking for a weighed value next cook.
- **Salt helpers:** use the house salt from `kitchen/pantry.md`.
- **Sanity-check ratios** after converting:
  - Bread dough: salt is usually ~1.8–2.2% of flour weight.
  - Dry brines: usually ~0.75–1.25% salt by weight of the meat.
  - Hydration should suit the style of bread.
  - If the source has something odd, flag it. Don't copy it silently.

## 4. Assign gear

- Read `kitchen/equipment.md` and pick each vessel by call name. **Check capacity against the actual volume:**
  - Simmering: no more than ~⅔ full.
  - Deep frying: oil no more than ~½ full.
  - Searing: the food must fit in a single layer.
- If nothing Brian owns fits, say so and suggest batching. Only note a gear idea if the gap will come up again.
- If the inventory is still empty, use generic equipment with sizes (`12" (30cm) cast iron skillet`) and mention that `/kitchen` would personalize it.

## 5. Write

- File: `recipes/<slug>.md`, kebab-case, no dates. Frontmatter and sections go in the order given in the format rules. New recipes start with `status: raw`, `version: 1`, `cooks: 0`.
- **Copyright:** credit the source in the frontmatter and under *Sources*. Write the method in our own words, never a pasted copy.
- Leave the persona out of the file. It should read like a clean, precise cookbook page.

## 6. Lint

Run the checklist in `recipe-format.md` every time. Actually go through it; don't check it from memory. At minimum, re-read the Method with the ingredient list open next to it and confirm:

- Every ingredient appears with its amount in the step that uses it, and divided portions add up to the total.
- No volume unit appears outside parentheses, and "teaspoon", "tablespoon", and "cup" are never spelled out as the main measure.
- Every temperature is written `°F (°C)`, and every time has a cue.
- Every call name exists in `kitchen/equipment.md`, and every vessel is big enough.

## 7. Index and commit

- Add or update the row in `recipes/README.md`, and remove the dish from *On deck* if it was listed there.
- Commit (see `.claude/rules/kitchen-tickets.md`):
  - New recipe: `feast: <title> v1`
  - Tweak or correction: `season: <title> v3, <what changed>`
- End with one line offering the natural next step: cook it now (`/cook`) or put it on a menu (`/menu`).
