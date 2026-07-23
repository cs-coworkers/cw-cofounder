---
repo: product-cofounder
task: T1
title: Get set up
absorbs: [old task 1, plugin install]
---

# T1 — Get set up

**The only task with no agent.** By the time this file is being read, the founder has already
done it: the app is installed, the folder exists, the plugin is installed, and they have said
*continue*. Everything below is therefore a **check**, not an instruction.

The founder-facing instructions for this task live outside the plugin, in the setup document
and install video — it is the one step that happens before any agent exists. That document
ends with:

> Say **continue** — you never need this document again.

## Gating questions

Ask only what cannot be seen. One question, once:

> Quick one before we start: is your Claude login saved in a password manager with
> two-factor turned on?

- Yes → record `password-manager: yes, 2FA on (attested T1, <date>)`.
- No → do not block. Say plainly: this is the one bit of housekeeping that gets expensive
  later, because a lot of accounts are coming. Offer to come back to it at the end of
  Task 2. Record `password-manager: not yet (asked T1, <date>)` and re-offer once, at T8,
  where the new Gmail account is created. Never nag a third time.

## verify-M

Passes when both of:

- A working folder is connected and writable. If not: stall `W1-T1-NO-FOLDER` or
  `W1-T1-NO-WRITE`.
- The plugin is loaded — self-evident, since this skill is the thing answering.

That is all. **The password-manager answer is deliberately not a verify condition.** It is a
question to ask, not evidence of work already done — and gating on it would mean a first run
over a founder's existing folder cannot credit T1 until they answer, which reports someone
four tasks in as being on task 1. Ask it when T1's flow runs; if it is unanswered, that is a
`needs-attention` note on T1, never a block on position.

Create `00-admin/` on the first successful pass and write the first `progress.md`.

## Success moment

> Your folder is connected and I can write to it. That's task 1 of 9 done — and it's the
> only one you had to do without me.
