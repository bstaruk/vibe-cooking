---
name: kitchen
description: Build and maintain Brian's kitchen inventory and cook profile. This covers equipment with sizes and call names, pantry defaults like the house salt, range and oven quirks, tastes, diet, and goals. Use it for the first-run kitchen tour. Also use it whenever Brian mentions gear that was bought, gifted, sold, broken, or retired ("I just got a Smithey No. 12", "the nonstick is dead"), shares photos of cookware or the pantry, or mentions a preference or constraint worth remembering.
argument-hint: "[tour | add <item> | remove <item> | profile]"
---

# /kitchen: inventory & cook profile

Request: `$ARGUMENTS`. If it's empty, work out the mode from context. If the kitchen files are still empty, offer the tour.

This skill keeps `kitchen/equipment.md`, `kitchen/pantry.md`, and `kitchen/profile.md` accurate. Every other skill relies on these files, so a wrong size here leads to a wrong recipe later.

## Call names

Every piece of equipment gets a **call name**. It's the short, unique name recipes and cook-alongs use.

- **Pattern:** size + maker + type. Examples: `3qt All-Clad saucier`, `12" Smithey skillet`, `5.5qt Staub Dutch oven`, `8" Misono gyuto`.
- **Twins:** if two items would share a call name, add something to tell them apart: `10" Griswold skillet (No. 8)` vs `10" Lodge skillet`.
- **Stability:** keep call names stable. If one has to change, grep `recipes/` and update every reference in the same commit.

## Mode: tour

Use this on first run, or when Brian says "let's do the kitchen tour."

Treat it as a conversation, not a form. Go one category at a time, ask 3–6 questions at once, and accept loose answers.

1. **Offer the photo shortcut first.** For example: "Snap your cookware shelf, knife block, and counter gadgets. I'll draft the inventory and you can correct me." Identify what you can from the photos. Mark sizes as `?` until Brian confirms them, and never estimate capacity from a photo.
2. **Look up specs fresh.** When Brian names a model ("All-Clad 3qt saucier"), search the web for the manufacturer's current specs: capacity, diameter, construction line (D3/D5/Copper Core…), oven-safe temperature, and induction compatibility. Confirm the exact variant with Brian, then record it.
3. **Tour order** (skip categories that don't apply):
   1. **Range & oven:** fuel (gas / induction / radiant / coil), burner sizes or BTU if known, convection, whether the oven runs true (suggest an oven-thermometer check if nobody knows), and hood strength (it matters for high-heat searing).
   2. **Cast iron:** maker, size or pattern number, and seasoning condition. For vintage pieces, record era, logo, markings, and where it came from. Brian loves this category, so act like a knowledgeable collector's assistant. For ID help, use the vintage references in `SOURCES.md`.
   3. **Carbon steel:** skillets and woks.
   4. **Stainless & clad:** saucepans, sauciers, sauté pans, stockpots. Record the construction line.
   5. **Enameled cast iron:** Dutch ovens, braisers.
   6. **Nonstick.**
   7. **Bakeware:** sheet pans, loaf and cake pans, pie and tart pans, bread cloches, baking stones or steels.
   8. **Knives & boards.**
   9. **Measuring:** scales (resolution: 1g vs 0.1g), thermometers (instant-read, leave-in probe, IR, oven), timers.
   10. **Countertop appliances:** stand mixer, food processor, blender, sous vide, pressure cooker, rice cooker, and so on.
   11. **Outdoor:** grill, smoker, pizza oven, griddle.
   12. **Pantry defaults:** house salt brand (it changes every volume helper), flours, butter, fats.
   13. **Profile:** who Brian cooks for and how often, diet, allergies, hard dislikes, favorite cuisines, dishes to master, weeknight time budget, spice tolerance, where Brian shops, and region/climate for seasonality (a general region is enough, since this repo is public).
4. **Write as you go.** Update the file after each category so nothing is lost if the session drops.
5. **Close the tour** with 2–3 observations in Patina's voice: strengths ("You've got thermal mass for days."), underused gear, or gaps. **Don't pitch purchases here.** If there's a real gap, add it to *Ideas* in `kitchen/wishlist.md` and leave it at that.

## Mode: add or update

1. If the model is known, look up its specs fresh and confirm the variant.
2. Add a row to the right table, with a call name. For vintage cast iron, include markings, era, and where it came from.
3. If it replaces something, move the old item to **Retired** along with the date and reason.
4. If it was on `kitchen/wishlist.md`, move it off the list and link the research report.
5. If the new gear makes a recipe or technique possible, mention one or two. It's Patina's way of welcoming it home.

## Mode: remove, broken, or retired

1. Move the row to **Retired** with the date and reason.
2. Grep `recipes/` for its call name. For each match, suggest a substitute Brian already owns (check capacity), then update the recipe after a quick OK.
3. If it leaves a real gap, add an entry to `kitchen/wishlist.md`.

## Mode: profile

Use this for changes to tastes, diet, goals, household, and stove or oven calibration. Any skill can also record these mid-conversation, per the working agreements in `CLAUDE.md`.

- If something was learned from a cook, date it and link the journal entry: `- Prefers more acid than most recipes call for (learned 2026-09-20, [journal](../journal/2026/2026-09-20-pan-sauce.md))`.
- Range and oven calibration goes in `kitchen/equipment.md` under **Range & oven**. Tastes and habits go in `kitchen/profile.md`.

## Finish

- Update the `_Last updated:` line in every file you changed.
- Commit the changes (see `.claude/rules/kitchen-tickets.md`), for example `chop: kitchen tour, cast iron & clad stainless`.
