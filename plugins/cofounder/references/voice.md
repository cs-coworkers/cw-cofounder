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

The verbs we **teach** are `cf-continue`, `cf-update`, `cf-status`. Write them that way every
time: in task files, in canned lines, in anything the founder pastes into their own settings or
instructions file.

The prefix is not decoration. A plain word can be claimed by any surface the founder's app
ships next, and when that happens the word stops reaching us — silently, with no error to
diagnose. That is not hypothetical: on 2026-07-24 a founder said "status" in Cowork, the host
matched it first and offered Claude Code instead, where the plugin is not installed, so nothing
happened at all. It also ends the "update my files" versus "update the plugin" ambiguity,
because only one of those two is `cf-update`.

**`cf-` is this product's namespace, not the company's.** It is the same prefix as the
product-level stall codes (`CF-NO-MARKER`, `CF-INPUTS-EMPTY`) — one token meaning "cofounder,
any week", covering both what the founder says and what we say back when something breaks.
Coworkers.Global's internal skills use `cw-`; keeping the two apart means a founder who one day
installs a second product of ours does not get two plugins competing for the same verb. Unique
against other vendors is not enough — this has to be unique against us too.

The skill names are the verbs, exactly: `cf-continue`, `cf-update`, `cf-status`. One name per
thing. The product namespace lives in the plugin name and the `product-cofounder` tag, not in
the skill name.

The bare words stay live as **silent aliases** in each skill's trigger list — a founder who
types "continue" out of habit still gets served, on any surface that lets the word through.
Never teach them, never print them, and never correct a founder who uses one. The prefixed
verb is the one we promise; the bare word is a courtesy that may stop working without notice.

**Any new verb, in any future week, carries the prefix.** No exceptions, no case-by-case
judgement about whether a particular word looks safe — that judgement is what failed here.

**And the prefix alone is not enough — screen the word after it.** Corrected 2026-07-27, on
evidence from the second install run: `cf-continue` and `cf-update` fired clean, while
`cf-status` rendered the map *and then* offered to switch to Claude Code. The host finds the
word it claims **inside** our prefixed token. So the prefix does not make a verb ours; it
demotes the failure from silent (the host wins outright, we never hear the founder) to noisy
(we answer, the host also interrupts). That is a real improvement and it is not immunity.

Both conditions, not either:

1. The verb carries `cf-`.
2. The word after the prefix is not one the founder's app claims — established by saying it on
   a real seat, not by reasoning about whether it sounds generic.

Condition 2 is not the case-by-case judgement the 2026-07-24 ruling rejected. That was picking
a plain word because it *looked* safe, with nothing to check it against. This is an observation
on a live surface with a yes-or-no answer: either the host reacted or it did not. Run it before
the verb reaches any founder-facing document — a verb is far cheaper to change before it is
taught than after, and `cf-status` is already in a recorded video.

Known claimed: **status**. Known clear: **continue**, **update** (Cowork, 2026-07-27). Extend
these lists as weeks ship rather than re-deriving them each time.

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

> Say **cf-status** to see where you are.

## The two lines that must appear

Once, in Task 4, exactly when the founder has just watched their material get distilled:

> Add files to `02-inputs/` whenever you like — then say **cf-update** and I'll take them in.

And at the end of Task 1's document, as its final line:

> Say **cf-continue** — you never need this document again.
