---
repo: product-cofounder
---

# Reconciliation — the spine

Fresh install and hundredth rerun are the same code path: **look at what is actually
there, then act on the gap.** Nothing in this protocol trusts a claim of progress.

Run this at the top of every `cofounder-continue`, and in read-only form for `cofounder-status`.

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
   Week 1; never read a week number out of `progress.md` and trust it.
   - `current-week` = the lowest-numbered installed week not fully `verified`/`skipped`.
   - `progress.md` has a `## Week N` section for a week that is **not** installed → do not
     delete it and do not re-derive it. Mark that week `not-installed`, stall
     `CF-WEEK-NOT-INSTALLED`, and point at `upgrade.md`. Their history stays.
   - Every installed week complete → there is no current task. Skip to step 7, congratulate
     plainly, and read `${CLAUDE_PLUGIN_ROOT}/references/upgrade.md` for what to say next.
     Do not invent a next task and do not imply the program is over.

4. **Run every mechanical verify block in the current week, against the filesystem.** Every
   run, all of that week's tasks — not just the current one. This is what catches state that
   broke three tasks ago. Each task's block is in `tasks/week-<N>/T<n>-*.md` under
   `## verify-M`. A block passes only on evidence: the file exists *and* contains what the
   block names. A file that exists but is empty, or is missing a required section, is
   `needs-attention`, never `verified`.

   **Weeks already complete are not re-verified.** Read their sections, carry them forward
   verbatim. A later release may ship changed task files; re-running old verify blocks
   against them would downgrade work the founder genuinely finished.

5. **Compare against what progress.md claimed.** Three cases:
   - *Agreement* — carry the stored `started` / `verified` dates forward unchanged. They
     are the time-actuals; never overwrite a real date with today's.
   - *Claimed done, evidence missing* — downgrade to `started` or `needs-attention` and
     **say so out loud**, naming the file that is missing. Do not silently correct.
   - *Evidence present, not claimed* — upgrade to `verified` and give partial credit
     out loud ("your concept file is already there and it checks out — that's task 5
     done"). This is the path a half-finished folder from the previous version takes.

6. **Rewrite progress.md** in the grammar of `state-contract.md`. This is the one file
   the protocol owns and may overwrite without asking. Rewrite the current week's section;
   carry every other section forward unchanged.

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
   `cofounder-status` gives it to them.

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

Say **status** to see where you are. If this keeps happening, send Charlie that code.
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
| `W1-T1-NO-FOLDER` | No working folder is connected to this project. |
| `W1-T1-NO-WRITE` | Folder connected but not writable. |
| `W1-T2-NO-CHROME` | Claude in Chrome not installed or not responding. |
| `W1-T4-CHROME-DEAD` | Site read failed — extension connected but page unreachable. |
| `W1-T4-INPUTS-EMPTY` | `02-inputs/` exists but has nothing in it. |
| `W1-T4-UNREADABLE` | An Inputs file could not be read (format or size). |
| `W1-T8-NO-CONNECTORS` | Connector list came back empty after the founder said they wired them. |

Add a code rather than failing quietly. A new failure mode with no code is a bug in this file.
Before adding one, decide which namespace it belongs in: *could this fire in Week 4?* If yes
it is `CF-`, whatever task surfaced it.
