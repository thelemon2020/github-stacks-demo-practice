# github-stacks-demo-practice

Rehearsal copy of [github-stacks-demo](https://github.com/thelemon2020/github-stacks-demo).
Same content, same structure, same `gh stack` registration — run through the
whole talk here as many times as you want. Nothing here is the copy you'll
actually present from; break it freely.

```bash
gh extension install github/gh-stack
```

See [DEMO_SCRIPT.md](DEMO_SCRIPT.md) for the walkthrough.

Open PRs:

- Real stack (via `gh stack`, tracked as stack #4): #1 → #2 → #3
- Traditional chain (plain branch-off-branch, squash-merged to show the break): #5 → #6 → #7
- Conflict demo: #8
- Retrofit pair (plain branch-off-branch, linked into a stack live via `gh stack link`): #9 → #10

## Resetting after a run-through

Once you've merged things and want to rehearse again, easiest is to delete
this repo and ask Claude to rebuild it — it's scripted, takes under a
minute. Don't bother trying to un-merge PRs by hand.
