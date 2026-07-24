---
repo: product-cofounder
---

# Reconciliation — the spine

Fresh install and hundredth rerun are the same code path: **look at what is actually
there, then act on the gap.** Nothing in this protocol trusts a claim of progress.

Run this at the top of every `cf-continue`, and in read-only form for `cf-status`.

## The loop

1. **Locate the venture folder.** It is the working folder connected to this project.
   If no folder is connected, stop with stall `W1-T1-NO-FOLDER` (see below) — the
   founder is not past Task 1 and nothing else can be checked.

2. **Read state, provisionally.** `00-admin/progress.md` and `00-admin/founder-profile.md`
   if they exist. Missing is normal on a first run; do not create them yet.

   **Then check for `CW-COFOUNDER-LOADED` in your own instructions.** This is the read receipt
   for the one step that cannot be inspected directly — the settings-field paste in T2.
   - Present → the paste landed. Say nothing; it is plumbing.
   - Absent, and T2's paste step has already run in an earlier session → stop here, stall
     `CF-NO-MARKER`, and re-print the four lines from `tasks/week-1/T2-meet-your-cofounder.md`.
     Do not advance the week on a broken push layer.
   - Absent, and the paste happened this same session → normal. Settings reach the agent on
     the next session. Carry on and check again next time.
   - Absent, and T2 has not run yet → normal. Carry on.

3. **Resolve the week.** List `${CLAUDE_PLUGIN_ROOT}/references/tasks/week-*/` — those
   directories, and only those, are the weeks this installed copy carries. Never assume
   Week 1; never read a week number out of `progress.md` and trust it. Then take the **first**
   of these that applies, in order — they are a precedence ladder, not independent bullets:

   - **(a) State names a week this copy does not carry.** `progress.md` has a `## Week N`
     section for a week not in the installed list. This wins over everything below, because a
     founder on an older release who has *already run* a later week must be told to update, not
     congratulated. Do not delete or re-derive that section (see step 6 for how it is written).
     Stall `CF-WEEK-NOT-INSTALLED`, point at `upgrade.md`, and frame it as "you're on an older
     version that's missing Week N — here's how to get it back", never as a fresh offer. Set
     `current-week` to the highest *installed* week so `progress` still renders something real.
   - **(b) An installed week has open work.** `current-week` = the lowest-numbered installed
     week not fully `verified`/`skipped`. This is the normal path; go on to step 4.
   - **(c) Every installed week is complete and state names no uninstalled week.** There is no
     current task. Skip to step 7, congratulate plainly, and read
     `${CLAUDE_PLUGIN_ROOT}/references/upgrade.md` for what to say next — offer the next week
     as new. Do not invent a task and do not imply the program is over.

   **Completion for (c) must have been earned once.** "Every installed week complete" is read
   from state, and state can lie. Before treating the top installed week as done-and-dusted,
   confirm its verify blocks still pass on this run (step 4 runs for the top installed week
   even when state calls it complete). Only a week *below* the top installed week is trusted
   from state without re-verifying (the "don't re-verify completed weeks" rule in step 4).

4. **Run every mechanical verify block in the current week, against the filesystem.** Every
   run, all of that week's tasks — not just the current one. This is what catches state that
   broke three tasks ago. Each task's block is in `tasks/week-<N>/T<n>-*.md` under
   `## verify-M`. A block passes only on evidence: the file exists *and* contains what the
   block names. A file that exists but is empty, or is missing a required section, is
   `needs-attention`, never `verified`.

   **A verify condition that depends on an unanswered gating question is not a failure.** Some
   blocks are conditional on a profile answer (T4's `site-summary.md` only if `website: yes`).
   If `founder-profile.md` does not exist yet, or that answer is unrecorded, the condition is
   *unknown*, not failed — leave the task `started`/`needs-attention` and let its flow ask the
   question. Never mark a task `not-started` because a branch you cannot yet evaluate is absent.

   **Which weeks get re-verified.** Always re-verify the **top installed week** — the highest
   week number this copy carries — even when state calls it complete; that is the one whose
   "done" decision gates whether you congratulate and offer the next week, and it must be
   evidence-backed every run, not trusted from a file the founder could have emptied. Weeks
   **below** the top installed week are read from their sections and carried forward verbatim,
   never re-verified: a later release may ship changed task files, and re-running old verify
   blocks against them would downgrade work the founder genuinely finished.

5. **Compare against what progress.md claimed.** Three cases:
   - *Agreement* — carry the stored `started` / `verified` dates forward unchanged. They
     are the time-actuals; never overwrite a real date with today's.
   - *Claimed done, evidence missing* — downgrade to `started` or `needs-attention` and
     **say so out loud**, naming the file that is missing. Do not silently correct.
   - *Evidence present, not claimed* — upgrade to `verified` and give partial credit
     out loud ("your concept file is already there and it checks out — that's task 5
     done"). This is the path a half-finished folder from the previous version takes.

6. **Rewrite progress.md** in the grammar of `state-contract.md`. This is the one file
   the protocol owns and may overwrite without asking. Rewrite the section for the week you
   re-verified this run (the top installed week — see step 4). Carry every **installed** week
   below it forward unchanged. For a week named in state but **not installed** (case 3a),
   replace its task rows with a single `not-installed` line and leave its heading — never
   delete the section, never keep stale task rows that imply the week is runnable here. This
   is the one exception to "carry other sections unchanged", and it is the same rule the state
   contract states; the two must not drift.

7. **Derive position** — within `current-week`, the first task that is neither `verified`
   nor `skipped`.

8. **Announce.** Plain language, no jargon:
   > Week 1 — task 4 of 9. Verified through task 3.
   > Next: feeding me everything you know about the business.

   **If any task *after* the current position has work in it, say so before the position
   line — this is mandatory, not optional.** Position is the first unverified task, so on a
   folder that was worked out of order it lands early and, said bare, reads as "you have
   done almost nothing". That is precisely the founder who has done most of five tasks and is
   about to quit. Credit the downstream work explicitly and by name:

   > Good news first: your concept file is two-thirds written and three of your four company
   > files are there. None of that is lost — I've counted all of it.
   >
   > Week 1 — the earliest thing still open is task 2 of 9, and it's a two-minute fix.
   > Next: adding one line to your instructions file so I start every session properly.

   Rules for the credit line: name the actual artifacts, never a count alone; say plainly
   that nothing is lost; keep the tone matter-of-fact, not congratulatory. If nothing
   downstream exists, omit it entirely rather than inventing encouragement.

9. **Run the current task's flow** from its `tasks/week-<N>/` file. One task visible at a
   time — do not preview later tasks, do not list the whole week, and never mention weeks
   that are not installed. If the founder wants the map they will ask, and
   `cf-status` gives it to them.

## Do no harm

- **Never overwrite anything the founder wrote.** If a task needs to change an existing
  artifact, show found-versus-needed and ask first:
  > Your `concept.md` has the one-line and one-paragraph sections but not the one-page
  > section. I can add the missing section and leave everything else exactly as it is —
  > want me to?
- **Never delete.** Not files, not sections, not rows.
- **Never tidy.** A v1 folder that has `CW1Tasks.md` and a different structure is not a
  mess to clean up; it is evidence. Read it, credit what it proves, leave it in place.
  `CW1Tasks.md` specifically: read its ticked boxes as *hints about where to look*, never
  as verification. A ticked box with no artifact behind it is `not-started`.
  Say once, on the first run over a v1 folder, that the old file is now inert — otherwise it
  sits there looking authoritative and the founder keeps ticking it:
  > You've got an older task file in here from the first version. It isn't driving anything
  > now — I track where you are from your actual files. I'll leave it exactly where it is.
- **Never re-ask a settled question** (`founder-profile.md`), and never infer one.

## Stall messages — no silent failures

Every path that stops emits a visible message the founder can copy to us verbatim. Format:

```
I'm stuck, and this isn't something you did wrong.

  What I tried: <plain sentence>
  What happened: <plain sentence>
  Code: W1-T4-CHROME-DEAD

Say **cf-status** to see where you are. If this keeps happening, send that code back to whoever set you up.
```

Codes come in two namespaces, uppercase, no spaces:

- **`CF-<reason>`** — product-level: the failure belongs to the plugin as a whole and can
  fire in any week. These names must never carry a week number, because they outlive one.
- **`W<week>-T<task>-<reason>`** — task-level: the failure belongs to one task in one week.
  Week-keyed on purpose — `W2-T3-…` is self-describing when a founder quotes it at us.

Existing codes:

| Code | Means |
|---|---|
| `CF-NO-MARKER` | `CW-COFOUNDER-LOADED` missing from instructions a session after the paste step — the settings pointer did not land. |
| `CF-STATE-CONFLICT` | `progress.md` cannot be parsed; rebuilt from evidence. |
| `CF-WEEK-NOT-INSTALLED` | `progress.md` has a week this installed copy does not carry. Their history is kept; see `upgrade.md`. |
| `CF-INPUTS-EMPTY` | `02-inputs/` exists but has nothing in it. Fires from T4 and from `update`, in any week. |
| `CF-UNREADABLE` | An inputs file could not be read (format or size). Fires from T4 and from `update`, in any week. |
| `W1-T1-NO-FOLDER` | No working folder is connected to this project. |
| `W1-T1-NO-WRITE` | Folder connected but not writable. |
| `W1-T2-NO-CHROME` | Claude in Chrome not installed or not responding. |
| `W1-T4-CHROME-DEAD` | Site read failed — extension connected but page unreachable. |
| `W1-T8-NO-CONNECTORS` | Connector list came back empty after the founder said they wired them. |

Add a code rather than failing quietly. A new failure mode with no code is a bug in this file.
Before adding one, decide which namespace it belongs in: *could this fire in Week 4?* If yes
it is `CF-`, whatever task surfaced it.
