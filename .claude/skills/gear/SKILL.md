---
name: gear
description: Research, compare, and decide on kitchen gear using fresh web research. Covers cookware (especially vintage and modern cast iron and carbon steel), knives, thermometers, scales, appliances, outdoor cookers, and gadgets. Use it whenever Brian asks about buying, upgrading, comparing, or evaluating gear ("is X worth it", "best Y right now", "what's new in Z"), wonders whether a tool would help, or wants to identify or value vintage cast iron. Never answer from training data alone.
argument-hint: "[question or product]"
allowed-tools: WebSearch WebFetch
---

# /gear: research & decisions

Question: `$ARGUMENTS`

Brian is a gear nerd. Act like a trusted friend who happens to run a testing lab: current data, honest verdicts, no sales pitch.

## Rules

- **Always research fresh.** Products get revised, discontinued, recalled, re-coated, and repriced, and companies get acquired. Search now, even if you think you know the answer, and date every price and availability claim.
- **Check timeless gear too.** A vintage Griswold doesn't change, but market prices, fakes and reproductions, and ID tips are worth a current look.
- **Start from the job, not the product.** Pin down the problem first: what's frustrating Brian or what the gear would make possible, plus the constraints (range type, storage, budget, weight, cleanup).
- **Check what Brian owns first.** Read `kitchen/equipment.md`. If something there already does the job, say so up front. The best gear is often already in the cabinet.
- **Build on past research.** Read `kitchen/wishlist.md` and look in `research/`. If we've researched this before, start from that report and refresh anything past its `refresh_after` date. If we *passed* on something, respect that reason unless something has changed.
- **Weigh sources.** Rank them in this order (see `SOURCES.md`, Gear sections):
  1. Independent long-term testing
  2. Experienced owner communities
  3. Manufacturer specs (trust the dimensions, not the marketing)
  4. Affiliate listicles (leads only, never evidence)
- **Suggest, don't sell.** An unprompted gear suggestion needs evidence behind it: a limitation we've actually hit (in the journal), a technique Brian wants to learn (in the profile), or a genuinely meaningful upgrade. Follow the limit set in `PATINA.md`.

## Workflow

1. **Frame the question** in 1–2 lines: the job, the constraints, and what Brian already owns. Only ask a clarifying question if the answer would change the recommendation (budget, induction vs gas).
2. **Research.**
   - For a quick factual question (a spec, a price, "is X still made?"), search directly.
   - For a real comparison or purchase decision, launch `kitchen-scout` subagents in parallel, one per contender or angle. Example: "Smithey No. 12 vs Field No. 10 vs vintage Griswold No. 8: current price, weight, cooking-surface finish, long-term owner reports." Give each scout the job, the constraints, and what Brian owns.
3. **Deliver the verdict, top first:**
   - **Verdict:** 1–2 sentences in Patina's voice.
   - **Comparison table:** model · price (with date and retailer) · key specs (weight, dimensions, material, induction and oven limits) · strengths · dealbreakers.
   - **Consider instead:** a vintage or used option, or "you already own X."
   - **Sources:** linked and dated.
4. **Record it.**
   - For anything substantial (a real comparison or a buy decision), write `research/YYYY-MM-DD-<topic>.md` using the format below, and add or update the entry in `kitchen/wishlist.md` (Researching, Wanted, or Passed).
   - A quick answer doesn't need a report. If you learned a lasting fact, add it to the equipment row or wishlist entry.
5. **If Brian buys it,** hand off to the `/kitchen` add flow (call name, specs, remove from the wishlist) and set `decision: bought` in the report.
6. **Ship it** following `.claude/rules/kitchen-tickets.md`: `forage(gear): <summary>`, or `stock(kitchen): …` when it's a purchase.

## Research report format

~~~markdown
---
topic: Carbon steel wok for induction
date: 2026-09-13
refresh_after: 2027-03-13
decision: undecided   # undecided · wanted · bought · passed
---

# Carbon steel wok for induction

## The job
The problem this solves, and the constraints (range, storage, budget, cleanup).

## Already in the cabinet
What we own that overlaps, and why it does or doesn't cover the job.

## Contenders
| Model | Price (date, where) | Specs | Strengths | Dealbreakers |
|---|---|---|---|---|

## Verdict
The recommendation, and what would change it.

## Sources
- [Title](url): what it contributed (accessed 2026-09-13)
~~~
