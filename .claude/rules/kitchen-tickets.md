# Kitchen tickets

These are our commit messages: a cheeky nod to Conventional Commits. There's just enough structure to make the history easy to scan, and not so much that anyone has to think hard about it.

## Prefixes

| Prefix | A nod to | Use it when we… |
|---|---|---|
| `feast:` | `feat:` | made something new: a recipe, technique note, menu, gear research, a skill |
| `season:` | `fix:` / `refactor:` | learned or adjusted something: a cook log, a recipe tweak, a correction, a change to the rules or persona |
| `chop:` | `chore:` | did prep work: kitchen inventory, sources, setup, indexes, typos, anything else |

**Can't decide in two seconds? Use `chop:`.** Nobody's grading.

## Format

- Write `<prefix>: <summary>` in lowercase, with no trailing period, in 72 characters or fewer.
- Add a body when the reason isn't obvious. For debriefs, say where the lessons were recorded.
- If a change affects how we work (for example, a rule change that means migrating existing files), add a `!`: `season!: temps go °C first`. Then use the body to explain what changed. Behind!

## Examples

~~~
feast: cast iron skillet cornbread v1
feast: carbon steel wok research
season: cornbread cook #2, 4/5
season: cornbread v2, pull at 21 min in the 12"
season: wit up to 6
chop: kitchen tour, cast iron & clad stainless
chop: add 12" Smithey skillet
chop: tidy sources tables
~~~

## Branches

- **Never commit on `main`.** Everything reaches `main` through a pull request that Brian reviews and merges.
- **Starting from `main`:** run `git pull --ff-only`, then `git switch -c <short-slug>`. A prefix such as `feast/cornbread` is welcome but not required.
- **Already on a branch?** Run `gh pr view --json state` to check whether it has been merged.
  - If it has merged, switch to `main`, pull, and start a new branch.
  - Otherwise, keep committing on the current branch. One branch can hold several units of work.
- **Commit locally** whenever a unit of work is done. There's no need to ask first.
- **Every commit lands on `main`.** PRs are rebase-merged, so each commit becomes a permanent ticket in the history. Don't make `wip` commits or "fix the last commit" commits. To fix a commit that hasn't been pushed yet, amend it. Never rewrite commits that have already been pushed.
- **Only push or touch a pull request when Brian explicitly asks** (see `CLAUDE.md`). If Brian asks for a push to a branch with an open PR, update the PR's title and description if they're out of date.
