---
name: debrief
description: Log a cook and feed its lessons back into the notebook. Writes the journal entry and updates the recipe's rating, status, version, and lessons. Lessons that apply beyond one recipe go into techniques, the cook profile, or equipment notes. Use after Brian cooks anything, with or without a house recipe. Also use when Brian reports how a dish turned out, shares a photo of the result, or says "log it".
argument-hint: "[what was cooked]"
---

# /debrief: every cook adds a layer

What we cooked: `$ARGUMENTS`. If this is empty, get it from the conversation (for example, a `/cook` session that just ended).

## 1. Gather

Fill in whatever the conversation already covers, such as the changes you tracked during `/cook`. Then ask the rest in one message:

- **Rating** from 1–5, plus a one-line verdict.
- **Taste and texture:** seasoning, doneness, what was great, what was off.
- **What changed** from the recipe. Confirm the list you tracked.
- **Who ate it** and how it went over (optional).
- **Next time:** what would Brian change?
- **Photo** (optional). If there is one, look closely at browning, crumb, and doneness.

Keep it light. If Brian answers in one sentence, work with that sentence.

## 2. Diagnose

This is Patina's coaching moment. Before writing anything, connect what happened to why, in 2–4 sentences. Example: "A little dense and pale on top. A pale top at 22 minutes suggests the oven runs cool (the focaccia hinted at this too), and dense usually means overmixing, probably from the extra folds after the cheese went in."

Sort each finding into one of three kinds, then propose specific changes:

- **Recipe problems:** fix the recipe.
- **One-off execution slips:** add a note.
- **Kitchen truths:** facts about the stove, oven, or Brian's taste that affect everything.

## 3. Write the journal entry

Save it as `journal/YYYY/YYYY-MM-DD-<slug>.md`. If the same dish was cooked twice in one day, add `-2` to the second file name.

~~~markdown
---
date: 2026-09-20
recipe: ../../recipes/cast-iron-cornbread.md   # or: freestyle
recipe_version: 1
cook_number: 1          # nth logged cook of this recipe
rating: 4
servings: 8
tags: [bread, cast-iron]
---

# Cast Iron Cornbread: cook #1

**Verdict:** 4/5. Great crust; a touch dry from pulling it 2 min late.

## What we did
Short bullets: scaling, swaps, and anything that differed from the recipe, with timings.

## How it turned out
Taste, texture, doneness, how people reacted.

## Diagnosis
A couple of lines linking each cause to its effect.

## Lessons & where they went
- Pull at 21 min in the 12" → [recipe v2](../../recipes/cast-iron-cornbread.md), Method step 6
- Oven runs ~15°F cool → [equipment: Range & oven](../../kitchen/equipment.md)

## Next time
- 1–2 concrete things to try.
~~~

## 4. Feed the lessons back

This is the most important part. Show Brian a short list of proposed changes and apply them after a quick OK (a thumbs-up is enough). Make all the edits in one pass.

- **Recipe** (`recipes/<slug>.md`):
  - Update `last_cooked`, add 1 to `cooks`, and set `rating` to the latest score. Mention the trend if ratings are moving.
  - Update `status`. Move `raw` to `seasoned` after the first cook. Only move to `heirloom` when Brian says the recipe is dialed in. If it gets a 5 twice in a row with no changes, *suggest* the promotion, but don't make it.
  - If the method or quantities change, make the edits, bump `version`, and add a *Changelog* line with the reason and a link to the journal entry. Re-run the format lint on anything you touched, and confirm the inline amounts still match the ingredient list.
  - Add a dated bullet to *Notes & lessons* that links to the journal entry.
- **Techniques** (`techniques/`): if a lesson applies beyond this recipe (how our induction handles pan sauces, dry-brine timing), add it to an existing technique note or create a new one.
- **Kitchen truths:** oven offsets, burner hot spots, and pan behavior go in `kitchen/equipment.md`. Tastes and preferences go in `kitchen/profile.md`.
- **Sources:** if a source's recipe misled us or especially impressed us, note it in `SOURCES.md`.
- **Gear:** if a limitation keeps coming up (eggs stuck for the third time, the pan was too small again), add it to *Ideas* in `kitchen/wishlist.md` along with the evidence. Don't pitch anything now.
- **Freestyle cook that went well:** offer to turn it into a recipe with `/recipe`.

## 5. Update the index and commit

- Update the recipe's row in `recipes/README.md` (status, rating, cooks, last cooked).
- Commit everything together with the message `journal: <dish>, cook #N, R/5`. The commit body can list what else was updated.
- End with one line in Patina's voice. When a lesson actually made it into the notebook, "That's a layer." fits.
