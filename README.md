# vibe-cooking

yo dawg i heard you like cook in your code

A kitchen notebook that runs on [Claude Code](https://claude.com/claude-code). Brian cooks and **Patina** (Claude, playing the kitchen guru) guides. Everything we learn gets written down, versioned in git, and fed back into the next cook. Recipes get better each time we make them, the way cast iron gets better each time it's seasoned.

There's no app, no scripts, and no CI. It's just markdown, git, and a handful of skills.

The repo is public on purpose, as an example of working with AI on something other than code.

## How to use it

Open this repo in the Claude Code desktop app and talk:

- *"Let's do the kitchen tour."* ← start here
- *"What should I make Saturday for six?"*
- *"Turn this into a house recipe: https://…"*
- *"I'm cooking the cornbread now."*
- *"Dinner's done. 4/5, a little dry."*
- *"Is a new Smithey worth it over my vintage Griswold?"*
- *"Why did my pan sauce break?"*
- *"From now on, bold every timer."*

Claude picks the right skill on its own. If you'd rather call one directly, use the slash commands:

| Command | What it does |
|---|---|
| `/kitchen` | Tour and maintain the inventory (every pot with its size and call name), pantry defaults, and cook profile |
| `/gear` | Research gear with fresh sources, compare options, decide, and track the wishlist |
| `/menu` | Pick dishes and build a shopping list in grams plus a prep timeline |
| `/recipe` | Write, import, adapt, or scale a recipe into the house format |
| `/cook` | Live cook-along: mise en place card, then brigade-style step calls |
| `/debrief` | Log the cook and fold its lessons back into recipes, techniques, and the kitchen profile |
| `/learn` | Deep dive into a technique or the science behind it, saved as a note with experiments to try |
| `/season` | Retro: audit the notebook and tune the rules, skills, and persona |

## The loop

```
 ┌─▶ /menu          what are we cooking?
 │     ▼
 │   /recipe        write it the house way
 │     ▼
 │   /cook          brigade-style cook-along
 │     ▼
 └── /debrief       log it · fold lessons back into recipes, techniques, kitchen

     /season        every ~5 cooks: audit the notebook, tune the rules
     anytime        /gear · /learn · /kitchen
```

## House laws

- **Grams first.** Volume shows up only as helper text, in parentheses.
- **Quantities inline.** Steps say "whisk 200g bread flour and 30g rye flour," never "whisk the flours."
- **°F first, °C helper.** `425°F (220°C)`.
- **Real gear.** "Make this in the 3qt All-Clad saucier."
- **Fresh research.** Gear questions get current web research, not stale training data.

## Kitchen tickets

Work happens on branches and reaches `main` through pull requests. Commit messages are a cheeky nod to Conventional Commits, and there are only three prefixes:

| Prefix | A nod to | Use it for |
|---|---|---|
| `feast:` | `feat:` | something new: a recipe, technique, menu, or gear research |
| `season:` | `fix:` | something learned or adjusted: a cook log, a tweak, a correction |
| `chop:` | `chore:` | prep work: inventory, sources, setup, tidying |

Can't decide in two seconds? It's `chop:`. The full guide is in [.claude/rules/kitchen-tickets.md](.claude/rules/kitchen-tickets.md).

## What's where

```
├── CLAUDE.md          the brain: house laws, map, working agreements
├── PATINA.md          the persona, with tuning knobs
├── SOURCES.md         chefs, sites & books we trust, ranked
├── SEASONING.md       log of how our process has changed, and why
├── LICENSE            MIT (the setup)
├── LICENSE-CONTENT.md CC BY 4.0 (the content)
├── kitchen/           equipment · pantry · profile · wishlist
├── recipes/           house recipes + index + on-deck list
├── journal/           cook logs & photos, one per cook
├── techniques/        lasting know-how & the science behind it
├── research/          dated gear research reports
├── inbox/             drop zone for photos to process (gitignored)
└── .claude/
    ├── rules/         units.md · kitchen-tickets.md · photos.md (always on) · recipe-format.md (recipes)
    ├── skills/        kitchen · gear · menu · recipe · cook · debrief · learn · season
    ├── agents/        kitchen-scout (parallel web research)
    └── settings.json  pre-approved tools (push & PRs always ask)
```

## Tuning it

Everything here is meant to change. Tell Patina *"from now on…"* and the relevant rule gets updated and logged in [SEASONING.md](SEASONING.md). For a bigger rethink, run `/season` for a full retro. Patina's personality has tuning knobs (wit, brigade lingo, science depth) at the top of [PATINA.md](PATINA.md).

## A note on food safety

These are one home cook's notes, not professional advice. Some recipes deliberately go below USDA's headline temperatures, like a 131°F steak or a 150°F chicken breast. Whenever a recipe does that, it says so and gives the time-at-temperature numbers it relies on. Use your own judgment, and when in doubt, follow USDA guidance.

## License

- **The setup is [MIT](LICENSE).** Borrow the workflow for your own kitchen, or for anything else.
- **The content is [CC BY 4.0](LICENSE-CONTENT.md).** Share and adapt it with credit. [LICENSE-CONTENT.md](LICENSE-CONTENT.md) spells out which files are setup and which are content, and how to credit them.
- **Adapted recipes credit their sources,** and those original works remain their authors'.
