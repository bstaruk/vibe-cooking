---
name: learn
description: Deep-dive into a cooking technique, ingredient, or food-science question. Explain it at the right depth and save it as an evergreen technique note with our own numbers and experiments to try. Use when Brian asks why something happens or how to master something ("why do pan sauces break", "teach me lamination", "how does dry brining work", "carbon steel vs cast iron seasoning"), wants to understand a failure, or wants to run a kitchen experiment.
argument-hint: "[technique or question]"
allowed-tools: WebSearch WebFetch
---

# /learn: technique & science

Topic: `$ARGUMENTS`

## 1. Start with what we already know

- Look for an existing note in `techniques/`. If one exists, add to it instead of starting over.
- Search `journal/` for cooks where this topic came up. Our own results are the best evidence we have.

## 2. Research

- **Start with the top tiers of `SOURCES.md`,** especially the science-focused ones. A Harold McGee–level explanation beats kitchen folklore.
- **Search the web for current information** when the science or common practice may have changed (new studies, revised USDA tables, new techniques), or when products are involved. For well-established science, cite the standard references.
- **For a big topic,** run `kitchen-scout` subagents in parallel, each on a different angle: the mechanism, how experts do it, and common ways it fails.
- **Say so when experts disagree** or the science isn't settled. Don't invent a consensus.

## 3. Teach

Explain it in Patina's voice, matching the depth to the question:

- **TL;DR first:** the one thing to remember.
- **Why it works:** the mechanism in plain language, with real numbers (temperatures, percentages, times).
- **How we'll do it:** the practical method, adapted to Brian's actual gear and range.
- **How it goes wrong:** symptom → cause → fix.
- **An experiment,** when there's a question we can test. Describe a side-by-side with one variable changed, what to keep the same, and how to judge the result.

## 4. Write the note

Save it as `techniques/<slug>.md`:

~~~markdown
---
title: Dry brining
tags: [meat, salt]
confidence: established   # established · our-experience · experimental
updated: 2026-09-13
---

# Dry brining

**TL;DR:** one or two sentences.

## Why it works

## How we do it
Numbers, gear, and timing, adapted to our kitchen.

## Failure modes
| Symptom | Cause | Fix |
|---|---|---|

## Our results
- Dated bullets that link to journal entries. Leave this empty until we've actually done it.

## Experiments to try
- [ ] Hypothesis · variable · how we'll judge it

## Related
Links to recipes and other techniques.

## Sources
- [Title](url): what it contributed
~~~

- Add or update the note's row in the `techniques/README.md` index.
- Commit (see `.claude/rules/kitchen-tickets.md`): `feast: <topic>` for a new note, or `season: <topic>` when adding to an existing note.
- If there's an experiment, offer to schedule it: add it to *On deck* in `recipes/README.md`, or plan it with `/menu`.
