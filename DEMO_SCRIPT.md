# Live demo script (practice copy)

Same script as the real repo, renumbered for this copy's PRs. Uses the
official [`gh stack`](https://gh.io/stacks) extension
(`gh extension install github/gh-stack`). Clone this repo and run
`gh stack checkout 4` (or any PR/branch in it) to get the stack checked
out locally.

## Cast

- **The stack** — [#1](../../pull/1) → [#2](../../pull/2) → [#3](../../pull/3)
  (`stack/1-kind-of-blue` → `stack/2-head-hunters` → `stack/3-love-supreme`),
  created with `gh stack submit`, linked as **stack #4** on GitHub.
- **The traditional chain** — [#5](../../pull/5) → [#6](../../pull/6) → [#7](../../pull/7)
  (`trad/1-rumours` → `trad/2-dark-side` → `trad/3-abbey-road`), plain
  `git checkout -b` + `gh pr create --base <branch>`, no `gh stack`.
- **The retrofit pair** — [#9](../../pull/9) → [#10](../../pull/10)
  (`retrofit/1-in-rainbows` → `retrofit/2-kid-a`), also plain, until Beat 6.
- **The conflict demo** — [#8](../../pull/8) (`demo/conflict-blue-train`),
  based on `main`, edits the exact same line as #1.

## Beat 1 — Show the real stack

Open #1, #2, #3. Point out the `N/3` badge and the "Stack created with
GitHub Stacks CLI" note. Open #6 (traditional chain) next to it — same
"wants to merge into a branch" shape, no stack UI.

```bash
gh stack view
```

## Beat 2 — A fixup ripples up cleanly

```bash
gh stack checkout 1
# edit RECORDS.md — tweak the Kind of Blue price
git commit -am "Fix Kind of Blue price"
gh stack submit --auto
```

Flip to #2 and #3 — diffs untouched.

## Beat 3 — Reorder the stack live

```bash
gh stack modify
```

Reorder so `stack/3-love-supreme` comes before `stack/2-head-hunters`,
Ctrl+S, then:

```bash
gh stack submit --auto
```

## Beat 4 — Atomic stack merge, one command

```bash
gh stack merge --yes --merge
```

## Beat 5 — Contrast: the traditional chain, by hand

Merge #5 with **"Squash and merge"** in the web UI. Flip to #6 — conflict /
polluted diff. Fix by hand:

```bash
git fetch origin
git checkout trad/2-dark-side
git rebase origin/main
git push --force-with-lease
```

Repeat for #7, or narrate it.

## Beat 6 — Retrofit an existing chain into a stack

```bash
gh stack link 9 10
```

Refresh #9 and #10 — real stack badges, zero local setup, PRs nobody built
with `gh stack` in the first place. Optionally `gh stack merge --yes` after.

## Beat 7 — Resolve a real conflict on camera

Merge #1 into `main` first (if not already merged from Beat 4). Then open
#8 (`demo/conflict-blue-train`) — genuine merge conflict, same insertion
point. Resolve live in GitHub's web conflict editor.

## Punchline

Same content, same branch-off-branch shape everywhere. The difference is
the tooling, not the topology — and per Beat 6, you can point that tooling
at history you didn't even build with it.
