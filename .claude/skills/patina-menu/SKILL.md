---
name: patina-menu
description: Decide what to cook and get organized. Suggests dishes, plans a meal, a week, or an event, and builds a consolidated gram-based shopping list with a prep timeline. Use when Brian asks what to make, wants ideas for an occasion or a number of guests, needs to use up ingredients, is planning a dinner party or holiday, or wants a shopping list.
argument-hint: "[occasion, guests, constraints]"
---

# /patina-menu: what are we cooking?

Request: `$ARGUMENTS`

## Gather context (read first, don't interrogate)

Before asking Brian anything, read:

- `kitchen/profile.md`: household, diet, tastes, time budget, region.
- `kitchen/pantry.md`: house defaults and staples. These stay off the shopping list.
- `recipes/README.md`: the *On deck* list, `raw` recipes still waiting for their first cook, and `heirloom` favorites.
- The last few `journal/` entries: what we cooked recently (avoid repeats), open "next time" notes, and experiments we planned.
- `techniques/`: any open *Experiments to try*.
- `kitchen/equipment.md`: gear that hasn't been used in a while makes a fun nudge ("the Staub hasn't braised anything since spring").

Then ask for only what's still missing, all in one message: how many people, when, how much time and effort, and any cravings or constraints.

## Suggest

- **Offer 2–4 options.** For each, give one line covering what it is, why now (season, a skill Brian wants to build, a recipe on deck, a lesson to try out), the effort, and the main gear.
- **Use today's date and Brian's region** to pick seasonal ingredients.
- **Include at least one proven dish.** When Brian is up for it, add one stretch option.
- **For events, plan around the actual range and gear.** Balance oven and burner use, and don't plan three dishes for one oven at three different temperatures.

## Build the plan (once Brian picks)

1. **Recipes:** use house recipes wherever they exist. For new dishes, offer to write them with `/patina-recipe` first so the cook-along has a solid recipe to follow.
2. **Shopping list:**
   - Combine quantities across dishes, in grams, with a count helper for produce: `450g yellow onions (~2 medium)`.
   - Group by store section: produce · meat & fish · dairy · bakery · pantry · specialty store.
   - Leave out the staples in `pantry.md`, and add a short "check you have" list at the end.
3. **Prep timeline:** work backward from serving time. Flag anything that needs to start a day or more ahead (dry brine, thawing, levain build, marinade, stock) with an absolute date and time, like "**Fri 7:00pm**: dry brine the chicken."
4. **Reminders:** if a step has to be done ahead and a scheduling or reminder tool is available in this session, offer to set a reminder. If not, put that step in bold at the top of the plan.

## Save the plan, or don't

- **Weeknight dinners and quick lists** stay in chat. No file.
- **Multi-dish events** (a holiday, a dinner party, a big cook day) get saved to `menus/YYYY-MM-DD-<event>.md` with the menu, timeline, and shopping list, then committed as `feast: <event> menu` (see `.claude/rules/kitchen-tickets.md`). After the event, `/patina-debrief` can log each dish and link back to the menu.
