# Changelog — `cofounder`

## 0.2.0 — 2026-07-23 (unreleased)

Repackaged as **one plugin that grows a week at a time** rather than a standalone Week-1
unit. No task content changed.

- Plugin renamed to `cofounder`; skills are now `cofounder-continue`, `cofounder-update`,
  `cofounder-status`. Tasks live under `references/tasks/week-1/`, with later weeks as
  siblings.
- Settings marker renamed to `CW-COFOUNDER-LOADED`. It is pasted into the founder's own
  settings field, so it must not carry a week number that would break at Week 2.
- Stall codes split into two namespaces: `CF-<reason>` for anything that can happen in any
  week, `W<week>-T<task>-<reason>` for a specific task in a specific week. New:
  `CF-WEEK-NOT-INSTALLED`. `W1-T4-INPUTS-EMPTY` and `W1-T4-UNREADABLE` became
  `CF-INPUTS-EMPTY` / `CF-UNREADABLE` — both fire from `update` as well as from T4, so
  neither belongs to Week 1.
- The session-start line the founder writes into their own instructions file, settings paste,
  and optional scheduled task now says "run the **continue** skill", with no week number. Same
  reason as the marker: it lives in state we do not own, and it would name the wrong week from
  Week 2 onward.
- A dead Claude in Chrome no longer strands the founder at T2. The stall code carries the
  unfinished business forward; the task itself verifies and position advances.
- Week resolution added. `progress.md` gains `weeks-installed` and `current-week` and keeps
  one section per week; weeks already finished are carried forward exactly as they were and
  are never re-checked against a later release's task files.
- `references/upgrade.md` added — how to pick up the next week, including the cached
  plugin-list behaviour that can hide a new version, warned about before it bites.
- `update` now disambiguates: the verb that re-reads your files and the button that fetches
  the next release share a word, so the agent asks rather than guessing.
- Versioning from here: **major version = week number** (Week 1 releases as `1.x`).
  Pre-release builds stay on `0.x`.

## 0.1.0 — 2026-07-22 (unreleased)

First build. Week One of Building With Managed Agents, delivered as a runnable protocol
instead of a task document.

- Three founder verbs as skills — at this version named `week1-continue`, `week1-update`,
  `week1-status` (renamed in 0.2.0).
- Reconciliation-first: every `continue` re-derives state from the artifacts actually on
  disk, so a fresh install and a hundredth rerun are the same code path.
- Nine tasks, one visible at a time, each with gating questions asked at the moment they
  matter, micro-steps with success moments, a mechanical check that gates advancement, and —
  where the artifact is a judgment call — a rubric that coaches but never blocks.
- `update` closes the structural gap in the document version: new files added to inputs can
  be re-ingested at any time and merged without clobbering earlier distillations.
- Never overwrites silently — found-versus-needed, then confirmation.
- Every stall emits a quotable code. No silent failures.
