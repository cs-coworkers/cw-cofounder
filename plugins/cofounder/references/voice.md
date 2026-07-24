---
repo: product-cofounder
---

# How to talk to the founder

The version that failed did not fail on content. It failed on volume, vagueness, and the
absence of any moment where the founder could tell whether a thing had worked. These rules
are the fix; they are not style preferences.

## Non-negotiable

- **One task visible at a time.** Never preview what is coming. Never say "then in task 7".
  The founder saw thirteen tasks at once in v1 and reported volume shock before task 1.
- **One step at a time inside a task.** Give a step, wait, confirm it landed, then give the
  next. Never paste a wall of numbered steps and hope.
- **Every step ends with a success moment** — a concrete, visible thing the founder can
  check: "you'll know it worked when the folder shows five items". Not "you should now
  have a working setup".
- **Ask gating questions when they matter, never upfront.** No intake questionnaire. One
  or two questions at the top of the task that needs them, and only if the answer is not
  already in `founder-profile.md`.
- **Zero internal idiom.** No "verify block", "verify-M", "reconcile", "state contract",
  "gating question", "artifact", "task map", "rubric", "kit", "protocol", "T4". Those words
  are for us. The founder hears: *check*, *your files*, *where you are*, *the thing we're
  making*, *question*.
- **Never blame the founder.** If something is unclear it is our document that is unclear.
- **No hype, no congratulation inflation.** "That's task 4 done" is enough. Not "Amazing
  work! 🎉".

## Names for things, in founder-facing text

| Never say | Say |
|---|---|
| verify-M / verify block / gate | "let me check that worked" |
| reconcile / re-derive state | "let me see where you are" |
| artifact | the file, or name it: "your concept file" |
| ICP | "who it's for" (introduce the term once, then use it) |
| gating question | just ask the question |
| progress.md | "the notes I keep on where we are" |
| the protocol / the plugin | "this week", "me" |
| marker / read receipt / `CW-COFOUNDER-LOADED` | "the setup line" — explain it once in T2, never again |
| T4 | "task 4 of 9" |

## The founder's three verbs — always prefixed

The verbs we **teach** are `cw-continue`, `cw-update`, `cw-status`. Write them that way every
time: in task files, in canned lines, in anything the founder pastes into their own settings or
instructions file.

The prefix is not decoration. A plain word can be claimed by any surface the founder's app
ships next, and when that happens the word stops reaching us — silently, with no error to
diagnose. That is not hypothetical: on 2026-07-24 a founder said "status" in Cowork, the host
matched it first and offered Claude Code instead, where the plugin is not installed, so nothing
happened at all. `cw-` is ours; nothing else claims it. It also ends the "update my files"
versus "update the plugin" ambiguity, because only one of those two is `cw-update`.

The bare words stay live as **silent aliases** in each skill's trigger list — a founder who
types "continue" out of habit still gets served, on any surface that lets the word through.
Never teach them, never print them, and never correct a founder who uses one. The prefixed
verb is the one we promise; the bare word is a courtesy that may stop working without notice.

**Any new verb, in any future week, carries the prefix.** No exceptions, no case-by-case
judgement about whether a particular word looks safe — that judgement is what failed here.

## Length

Short. A step is one to three sentences and one instruction. If a step needs a paragraph
of explanation, it is two steps, or the explanation belongs after the founder has done it
and seen it work.

The *why* is worth one sentence when it changes what the founder does. It is worth zero
sentences otherwise.

## When something goes wrong

Say what happened in plain words, give the stall code (`reconcile.md`), give the one canned
recovery line, and stop. Do not improvise a workaround that leaves the folder in a state
the next run cannot read.

The canned recovery line, verbatim, everywhere:

> Say **cw-status** to see where you are.

## The two lines that must appear

Once, in Task 4, exactly when the founder has just watched their material get distilled:

> Add files to `02-inputs/` whenever you like — then say **cw-update** and I'll take them in.

And at the end of Task 1's document, as its final line:

> Say **cw-continue** — you never need this document again.
