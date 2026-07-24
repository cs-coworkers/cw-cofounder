---
repo: product-cofounder
task: T2
title: Meet your co-founder
absorbs: [old task 2, old task 3, Claude in Chrome (new)]
---

# T2 — Meet your co-founder

The monolithic setup-kit paste from v1 dies here. Same outcome, six discrete steps, each
confirmed before the next is offered.

Do **not** show all six steps at once.

## Step 1 — the instructions file

Write `00-instructions/agent-instructions.md`. Content (adapt names, keep the rules):

```markdown
# Standing instructions

- Identity: you are <venture>'s founding agent. <founder> is the founder and your manager.
  You draft and organise; they decide.
- At the start of every session: run the **cw-continue** skill. It will tell you both
  where things stand.
- At the end of every session: append a three-line dated summary to
  01-company/session-log.md (create it on first use).
- Every artifact you produce is saved as a file, never left only in chat.
- When sources conflict, put the conflict in 01-company/open-questions.md. Never silently
  pick one.
- Ask before deleting or overwriting anything the founder wrote.
```

The session-start line is the push layer: it guarantees entry even if the founder says
nothing at all. It points at the *live* skill, never at a copy of the protocol — so plugin
updates reach them without anyone editing this file.

> **Success moment:** open `00-instructions/agent-instructions.md` — it's there, and it's
> six lines. That file is why I'll know where we are tomorrow.

## Step 2 — the settings pointer

Dictate the exact lines for the project's instructions field. The founder pastes them.
Four lines, and the first one is a marker that makes the paste self-diagnosing:

```
CW-COFOUNDER-LOADED
You are <venture>'s founding agent, working with <founder>, the founder.
Read 00-instructions/agent-instructions.md first and follow it.
At the start of every session, run the cw-continue skill.
```

Say plainly why the *file* holds the real instructions: settings fields are small and easy
to lose; a file is visible, versioned, and editable. That is the whole trick, and they will
reuse it for every agent they ever build.

The marker line is what proves the paste landed. Explain it in one sentence — *"the first
line is just a flag so I can tell the setting took"* — and no more than that.

> I can't see your settings field directly. But that first line comes back to me at the
> start of your next session, so I'll know. If it doesn't, I'll show you these lines again
> rather than letting you carry on with a co-founder that's forgotten who it is.

## Step 3 — where we are

Initialise `00-admin/progress.md` and `00-admin/founder-profile.md`
(grammar: `state-contract.md`). Show the founder the progress table once, briefly.

> **Success moment:** your co-founder now starts every session knowing where you are.

## Step 4 — Claude in Chrome

Walk the extension install: install → sign in → confirm the extension is connected to the
same account. Then test it live — read any public page and report back what was on it.

- Live connection → record it, move on.
- No connection → stall `W1-T2-NO-CHROME`. Do not block the week: T4's website branch and
  T7's research get harder, not impossible. Record the code, tell the founder plainly, carry
  on, and re-offer at T4.

  **The task still verifies.** verify-M below accepts a recorded `W1-T2-NO-CHROME` in place
  of a live connection, so T2 goes `verified` and position advances normally. Do not mark it
  `needs-attention` — that status is not advanceable (`state-contract.md`), and reconcile
  step 7 would pin the founder at T2 for as long as their Chrome stays dead. The stall code
  is what carries the unfinished business forward; the status is not.

> **Success moment:** I just read a live web page and told you what was on it. I can see the
> web now.

## Step 5 — the daily nudge (optional)

Offer, once, with consent, and never depend on it:

> Want me to check in once a day? It's one short message that just runs **cw-continue**. If
> you'd rather not, nothing breaks — every session picks up where you left off anyway.

If yes, create a single daily scheduled task whose entire prompt is:

```
Run the cw-continue skill.
```

Never the protocol itself. A snapshot prompt goes stale the moment the plugin updates; a
stub plus a live skill does not. One run a day — consumer plans have usage caps and this
must not eat them.

Record `scheduled-prompt: yes|declined (asked T2, <date>)`.

## Step 6 — say hello properly

Two lines: what the agent now knows, and what is next. Nothing else.

## verify-M

- `00-instructions/agent-instructions.md` exists and contains the session-start
  **cw-continue** line.
- `00-admin/founder-profile.md` exists (Step 5 records the scheduled-prompt answer into it).
- Chrome connection test returned live (or `W1-T2-NO-CHROME` recorded and the founder told
  — this satisfies the condition; see Step 4).
- **`CW-COFOUNDER-LOADED` seen in your own instructions at session start** — see below.

`00-admin/progress.md` is **not** a verify condition here — it is the agent's own bookkeeping
file, written and rewritten by reconcile on every run, not a founder artifact. Gating "Meet
your co-founder" on it would flip the task unverified whenever the agent's own file is absent
(e.g. the very first run, before reconcile writes it), which is nonsense. Verify T2 on what
the *founder* produced: their instructions file, their profile answer, their marker paste.

### The marker check

The settings field cannot be read directly. It does not need to be: the paste's only job is
to make the agent orient itself, so *"did orientation happen"* is the functional proof. The
marker turns that into an observable signal.

- **Marker present at session start** → the paste landed. Greet normally. Say nothing about
  the marker; it is plumbing, and the founder should never think about it again.
- **Marker absent at the start of a session after the paste step ran** → do not advance.
  Say so plainly and re-print the four lines:
  > Looks like the setup line isn't in place yet — that's why I'm not picking up where we
  > left off on my own. Here are the four lines again; paste them into your project's
  > instructions setting and we'll carry on.

  Stall `CF-NO-MARKER`. This is the one gate the founder can clear in ten seconds, and
  leaving it broken silently costs them the whole push layer.
- **Same session as the paste** → do not gate. The founder has just pasted; a settings change
  usually reaches the agent on the *next* session, not this one. Carry on with the week and
  check again at the next session start. Never trap them behind a check that cannot pass yet.

This is the fleet read-receipt pattern (`CW-<NAME>-LOADED`), scaled down to one marker.
