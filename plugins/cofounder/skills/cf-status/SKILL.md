---
name: cf-status
description: >
  Show the founder where they are, read-only. Use whenever the founder says "cf-status" — the
  taught verb — or any natural equivalent: "where am I", "how much is left", "show me the
  list", "what have I done", "is this thing working", "what's still open", "progress",
  "status", or asks to see all the tasks at once. Renders the current
  week's tasks with what is verified, what is next, and how to get help. Changes nothing.
---

# cf-status

The founder's "is this thing working?" button. **Read-only.** This skill never writes a file,
never advances a task, never asks a question.

**The taught verb is `cf-status`.** "status" and "progress" remain silent aliases in the
trigger list above, but never print them — this is the verb the host actually took from us
(Charlie's run, 2026-07-24: Cowork matched "status" first and offered Claude Code, where the
plugin is not installed, so nothing happened). Rule and rationale: `voice.md` § The founder's
three verbs. The skill's own name is unchanged; the founder never types it.

## Before you answer

Read `${CLAUDE_PLUGIN_ROOT}/references/voice.md`, then run the reconciliation loop from
`${CLAUDE_PLUGIN_ROOT}/references/reconcile.md` **in read-only mode** — resolve the current
week, check every task in it against what is on disk, but do not rewrite
`00-admin/progress.md`.

Include the `CW-COFOUNDER-LOADED` marker check. If the marker is missing and T2's paste step has
already run, say so here as a fixable line rather than a stall — `cf-status` never blocks:

> One thing to fix: the setup line isn't in your project's instructions setting, so I'm not
> starting sessions on my own. Say **cf-continue** and I'll give you the lines again.

If what you find disagrees with the stored progress file, show the truth from disk and say
one line about it:

> (Heads up — your notes say task 5 is done but I can't find the file. Say **cf-continue** and
> I'll sort it out.)

## What to show

The whole map **for the current week**. This is the one place the founder is allowed to see a
week's tasks all at once, because they asked. Weeks they have already finished get one summary
line each above the map; weeks that are not installed are never mentioned.

```
Week 1 — you're on task 4 of 9. Verified through task 3.

  1. Get set up                        done   20 Jul
  2. Meet your co-founder              done   21 Jul
  3. Run your screens                  done   21 Jul
  4. Feed your knowledge               in progress — started today
  5. Your concept at three zoom levels
  6. Who it's for
  7. The honest competitive snapshot
  8. Channels ready
  9. Face reality

Next: finishing task 4 — I've got 6 of your files, and I'm distilling them now.

Say **cf-continue** to carry on.
Add files to 02-inputs/ any time, then say **cf-update**.
Stuck? Send whoever set you up whatever I last told you, including any code like W1-T4-CHROME-DEAD.
```

Rules for rendering:

- Task titles in plain words, exactly as in the task files. Never `T4`.
- Skipped tasks show as `skipped — no website yet`, with the reason. Not as failures.
- `needs-attention` shows as `needs a look`, with one line saying what is missing.
- No percentages, no progress bars, no praise. A count and a next step.
- The three closing lines — continue, update, help — appear every time. They are the founder's
  entire interface, and repeating them costs nothing.

## If the current week is complete

Show the map with everything done, then one line pointing at the next week — the same steps
as `${CLAUDE_PLUGIN_ROOT}/references/upgrade.md`, said shorter because they only asked for
status:

> Week 1 — all nine done. Week 2 comes as an update to me; say **cf-continue** and I'll walk
> you through picking it up.

## If nothing exists yet

They have installed the plugin and said cf-status before anything else. That is fine:

> You're at the very start — nothing set up yet, which is exactly right.
> Say **cf-continue** and I'll take you through it, one step at a time.
