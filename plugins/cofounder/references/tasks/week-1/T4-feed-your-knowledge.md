---
repo: product-cofounder
task: T4
title: Feed your knowledge
absorbs: [old task 5, website ingestion (new)]
introduces: update verb
---

# T4 — Feed your knowledge

The biggest task of the week — roughly half a day of the founder's attention, and the one
that makes every later task smarter. Say the cost up front, honestly, before they start.

This task also **introduces the `update` verb**. That is not decoration: the absence of a
re-ingest verb is the structural bug that broke v1: a founder added documents to Inputs and had
no way to say "take these in". She asked out loud: *"what if I add more files?"* This task
answers that question before she has to ask it.

## Gating question — website

> Do you have a website for this yet?

- **Yes** → take the URL, read it with Claude in Chrome, and distil
  `01-company/site-summary.md`: what the site says the business is, who it addresses, what it
  offers, what it claims, and anything that contradicts what they have told you. Show it to
  them and ask if it is accurate — a site is often eighteen months stale.
  - Chrome not connected → stall `W1-T2-NO-CHROME`, offer the extension install again.
  - Page unreachable → stall `W1-T4-CHROME-DEAD`; offer to take a copy-paste instead.
- **No** → skip, record `website: no (asked T4, <date>)`, and say the branch stays open:
  *"tell me when you have one and I'll read it."*

Record the answer either way. Never ask again unprompted.

## Steps

**Step 1 — gather.** Everything: notes, decks, voice-memo transcripts, photos of napkins,
old plans, spreadsheets. Into `02-inputs/`. Repeat the exclusions from T3 in one line.

If their notes live in Google Docs, say so now: T8 wires Drive, and they can either do this
manually today or wire Drive first and come back. Either is fine; do not let them stall on it.

If they have nothing written — this is common and not a failure — switch to the interview
branch below.

> **Success moment:** tell me when the files are in and I'll tell you how many I can see.

**Step 2 — confirm receipt.** Count and list what is in `02-inputs/`. Name anything
unreadable rather than skipping it silently (`CF-UNREADABLE`). Empty folder →
`CF-INPUTS-EMPTY`.

**Step 3 — distil.** Write the four files in `01-company/`:

- `company-snapshot.md` — what this business is. One page maximum.
- `people.md` — every person mentioned: name, role, relationship, contact if known.
- `sources-index.md` — one line per source: what it is, its date, what it is good for.
- `open-questions.md` — every gap, contradiction and unresolved decision found.
  (This file already exists from T3. **Append; never overwrite the legal flags.**)

Rules: every summary line cites its source file. Conflicts go to `open-questions.md`, never
silently resolved. Each file small enough to read in two minutes.

If there are co-founders, note in `open-questions.md` who owns what IP so far. Do not try to
resolve it this week. Do not leave it unwritten either.

**Step 4 — the payoff.** Tell them the three most surprising things found. This is the moment
the week earns its keep — the founder discovers their own notes contradicted themselves.

**Step 5 — read them.** Ask them to actually open the four files. Then ask one question:
did anything in `open-questions.md` surprise you?

**Step 6 — the update line.** Say it, in these words:

> Add files to `02-inputs/` whenever you like — then say **cw-update** and I'll take them in.
> New files never wipe out what's already here; I'll show you what changed before I touch
> anything.

## No-documents branch

Interview them instead. One question at a time: the problem, who has it, how they found it,
what they have tried, who else is working on it, what they do not know yet. Stop when new
answers stop adding information. Write the same four files, with `founder interview` as the
source. Close with the three biggest gaps.

## When some of this already exists

A folder from the previous version usually has two or three of the four files. **Fill only
the gap.** Do not re-run the whole distil to produce one missing file: the existing files may
have been hand-edited by the founder, and rewriting them to "regenerate consistently" is the
silent overwrite this protocol exists to prevent.

- Missing file → write just that one, from the same Inputs.
- Existing file that looks thin → say so, offer to extend it, and wait. Never rewrite it
  because it does not match the shape you would have produced.
- Existing file citing a source no longer in `02-inputs/` → leave it, note it in
  `sources-index.md` as a source you cannot see.

## verify-M

- All four `01-company/` files exist and are non-empty.
- `sources-index.md` has at least one line per file in `02-inputs/` (or the interview line).
- `site-summary.md` exists **if** `website: yes`; absent is correct if `website: no`.
- `open-questions.md` still contains the T3 legal-flag sections — if the distil pass
  clobbered them, that is a bug: restore and report it.
- The founder has confirmed they read the four files.

## verify-J — coverage rubric (always delivered, never blocks)

Report honestly:

- Which files in `02-inputs/` fed which distilled file.
- Any Inputs file that could not be used, **and why** — wrong format, unreadable, empty,
  or out of scope. Never let a file sit unmentioned.
- Whether the snapshot rests on one source or several. One source is not a failure; it is
  worth them knowing.

## Success moment

> Four files, and I've read everything you gave me. From here on, every answer I give you
> is grounded in your material rather than my guesses. Task 4 of 9 done — that was the
> heavy one.
