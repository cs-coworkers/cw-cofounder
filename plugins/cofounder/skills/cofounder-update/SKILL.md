---
name: cofounder-update
description: >
  Re-ingest the founder's material. Use whenever the founder says "update", or tells you they
  have added, changed, or removed files in their inputs folder — "I've added more files", "what
  if I add more documents", "I put some new notes in there", "re-read my stuff", "I've updated
  the deck". Sweeps the inputs folder for anything new or changed and merges it into the
  distilled company files without overwriting what is already there. Safe to run any number of
  times, in any week.
---

# update

The founder has more material. Take it in without destroying what is already distilled.

This verb exists because its absence broke the previous version: a founder added documents to
her inputs folder and had no way to tell her agent to read them. If she is asking the question
at all, the answer is always yes — never tell her to wait for a later task.

**One word, two meanings — disambiguate before acting.** "Update" also names the step for
getting the next week (`${CLAUDE_PLUGIN_ROOT}/references/upgrade.md`), and the founder has no
reason to know the difference. If they say it right after being told a week is complete, or
alongside anything about a new week, versions, or installing — ask, in one line, before
sweeping anything:

> Two different things share that word — do you mean re-reading your files, or picking up the
> next week? Either way I've got you.

Any other time, they mean their files. Do not ask then; just run.

## Before you start

Read `${CLAUDE_PLUGIN_ROOT}/references/voice.md` and
`${CLAUDE_PLUGIN_ROOT}/references/state-contract.md`.

## The loop

**1. Sweep.** List everything in `02-inputs/`. Compare against `01-company/sources-index.md`,
which holds one line per source already ingested. Classify each file:

- **new** — not in the index;
- **changed** — in the index, but modified since (say so; do not guess silently);
- **unchanged** — skip, do not re-read;
- **gone** — in the index, no longer in the folder. Do **not** remove its contribution.
  Flag it: *"the file is gone but what I learned from it is still in your notes — tell me if
  it should come out."*

Nothing new or changed → say so plainly and stop. That is a successful run, not a failure.

Empty inputs folder → stall `W1-T4-INPUTS-EMPTY`.

**2. Read the new material.** Anything unreadable gets named, with the reason
(`W1-T4-UNREADABLE`). Never skip a file in silence.

**3. Work out what changes.** For each of the four `01-company/` files, and
`03-artifacts/` if the new material touches a saved artifact, decide what the new material
adds, contradicts, or supersedes.

**4. Show the diff before touching anything.** This is the step that makes the verb safe:

```
Three new files. Here's what changes:

  company-snapshot.md   + two lines about the pricing model (from pricing-v3.xlsx)
  people.md             + 4 people (from board-deck.pdf)
  sources-index.md      + 3 lines
  open-questions.md     + 1 conflict: the deck says 12 customers, your notes say 8

Nothing existing gets removed. Want me to go ahead?
```

Wait for a yes. If the founder says no, change nothing and say what you left alone.

**5. Merge — add, never replace.**

- Append new facts. Do not rewrite a section wholesale to accommodate one new line.
- **A contradiction is never resolved silently.** It goes to `open-questions.md` with both
  sources named and dated. That surfacing is the most valuable thing this protocol does.
- If new material genuinely supersedes old (a v3 that replaces a v1), say so explicitly,
  keep the old line in `sources-index.md` marked superseded, and ask before removing anything
  from a distilled file.
- Update `sources-index.md` with a line per newly-read file: what it is, its date, what it is
  good for.

**6. Report.** What was added, what conflicts surfaced, what you could not use and why. If
anything new is interesting, say so — this is a second chance at the surprise moment from
task 4.

## If the founder is not past task 4 yet

The distilled files may not exist. Do not error out. Say plainly that the material is safely
in the inputs folder and will be taken in when you get to that task — then offer to jump
straight to it if they would rather do it now.

## Website updates

If `founder-profile.md` says they have a website and they mention it has changed, re-read it
with Claude in Chrome and refresh `01-company/site-summary.md` under the same
show-the-diff-first rule.

## After any successful update

Say this, once:

> Done. Add more whenever you like — say **update** again and I'll take those in too.

Then offer to carry on with the current task. Do not restart the week and do not re-verify
tasks that were already verified; running `update` never moves position.
