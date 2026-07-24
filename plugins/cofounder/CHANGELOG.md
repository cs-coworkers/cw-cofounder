# Changelog — `cofounder`

## 0.3.0 — 2026-07-24 (unreleased)

**The three founder verbs are now `cw-continue`, `cw-update`, `cw-status`.** Breaking for
anyone mid-week: the wording in your own `agent-instructions.md`, settings paste, and daily
scheduled task changes. Say the bare word if you forget — it still works on most surfaces.

- Found on the first real run of the program: saying **status** in Cowork was matched by the
  host app before the plugin saw it, and offered Claude Code — a separate runtime where the
  plugin is not installed, so nothing happened at all. No error, nothing to diagnose.
- Any plain word can be claimed by whatever an app ships next, so the taught verbs now carry a
  prefix nothing else claims. The bare words stay as silent aliases: a founder who types
  "continue" out of habit is still served wherever the word gets through, but the prefixed verb
  is the one that is promised.
- Side benefit: the "update my files" versus "update the plugin" ambiguity disappears for the
  taught verb, because only one of the two is `cw-update`. The disambiguation question remains
  for the bare alias.
- The rule is written down rather than left to judgement — `voice.md` § The founder's three
  verbs, plus a line in `upgrade.md`'s release checklist so every future week's verbs inherit
  it. Gate 2's run book now tests the prefixed verb *and* records what the bare alias does.

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
