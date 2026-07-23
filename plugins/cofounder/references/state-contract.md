---
repo: product-cofounder
---

# State contract

All state lives in the **founder's venture folder**. The plugin is protocol only and is
read-only with respect to itself: reinstalling or updating it never touches state.

## Folder shape

```
<venture folder>/
  00-admin/
    progress.md          <- task state, agent-maintained, derived from artifacts
    founder-profile.md   <- settled answers to gating questions
  00-instructions/
    agent-instructions.md
  01-company/
    company-snapshot.md
    people.md
    open-questions.md
    sources-index.md
    capabilities.md      <- T8; what each connector can and cannot do
    site-summary.md      <- T4, only if the founder has a website
    session-log.md
  02-inputs/             <- the founder's raw material; they add to it any time
  03-artifacts/
    concept.md
    icp.md
    competitive-snapshot.md
    domains.md
    riskiest-assumption.md
```

Create folders and files only as the task that owns them runs. Do not pre-create empty
files — an empty file that looks done is exactly the failure mode this build exists to kill.

## `00-admin/progress.md`

Agent-maintained. Rewritten on every `continue` from what is actually on disk. Never edited
by hand, never trusted over evidence. Grammar is strict so it can be parsed on the next run.

```markdown
# Progress

<!-- Maintained by your co-founder. Re-derived from your files every session.
     Editing this by hand does nothing: the next check reads your actual files. -->

last-reconciled: 2026-07-22T14:05
weeks-installed: 1
current-week: 1
position: W1 T4 (task 4 of 9), verified through T3

## Week 1

| task | title              | status   | started    | verified   | artifacts |
|------|--------------------|----------|------------|------------|-----------|
| T1   | Get set up         | verified | 2026-07-20 | 2026-07-20 | 00-admin/, 02-inputs/ |
| T2   | Meet your co-founder | verified | 2026-07-20 | 2026-07-21 | 00-instructions/agent-instructions.md |
| T3   | Run your screens   | verified | 2026-07-21 | 2026-07-21 | 01-company/open-questions.md |
| T4   | Feed your knowledge | started | 2026-07-22 | —          | 02-inputs/ (6 files) |
| T5   | Your concept at three zoom levels | not-started | — | — | — |
| T6   | Who it's for       | not-started | —        | —          | — |
| T7   | The honest competitive snapshot | not-started | — | — | — |
| T8   | Channels ready     | not-started | —        | —          | — |
| T9   | Face reality       | not-started | —        | —          | — |
```

**Fields**

- `weeks-installed` — which weeks this installed copy of the plugin carries, derived from
  the `references/tasks/week-*/` directories that actually exist. Never stored as a claim;
  re-derived every run. A founder on an older release genuinely has fewer weeks.
- `current-week` — derived: the lowest-numbered installed week that is not fully
  `verified`/`skipped`. If every installed week is complete, it stays at the highest
  installed week and `continue` offers the upgrade path (`references/upgrade.md`).
- `task` — `T1`…`Tn`, **scoped to its week section**. Task numbers restart each week;
  `W1 T4` and `W2 T4` are different tasks. Within a week: never renumbered, never removed.
- `status` — exactly one of:
  - `not-started` — no evidence of any work.
  - `started` — some artifacts exist, mechanical verify does not pass yet.
  - `verified` — mechanical verify passes. The only status that permits advancement.
  - `skipped` — a gating question ruled the task out (e.g. no website). Records *why*
    in the artifacts column. Counts as advanceable; revisable at any time.
  - `needs-attention` — artifacts exist but conflict with what verify needs (e.g. a file
    present but missing a required section). Always accompanied by a stall message.
- `started` / `verified` — ISO dates. These are the week's time-actuals, and the reason this
  protocol records dates at all. Never back-fill a date you did not observe; use `—`.
- `artifacts` — comma-separated paths, relative to the venture folder.

`position` is derived, never stored independently: within `current-week`, the first task
that is not `verified` or `skipped`. Written `W<week> T<n>`.

**Weeks are sections, and completed weeks are never rewritten.** Each installed week gets
its own `## Week N` heading and table. When a new week arrives as a release, reconcile
appends its section — it does not touch the tables above it, and it does not re-verify
completed weeks against task files that may have changed between releases. A week that was
`verified` stays `verified`; its dates are time-actuals and they are the whole point.

A `## Week N` section for a week that is **not** installed is a real state, not corruption:
the founder ran that week and has since reinstalled an older release, or restored an old
folder. Keep the section, mark the week `not-installed` in place of task rows, and stall
`CF-WEEK-NOT-INSTALLED` rather than silently deleting their history.

## `00-admin/founder-profile.md`

Settled answers to gating questions, so a rerun never re-asks a question the founder has
already answered. Founder-readable and founder-revisable in plain language.

```markdown
# About you and this venture

<!-- Your co-founder asks these once, when they matter. Say "actually, that's changed"
     any time and the relevant task re-opens. -->

- venture-name: Kettle & Co
- founder-name: Robin
- website: yes — https://kettleandco.example  (asked T4, 2026-07-22)
- domain-owned: yes — kettleandco.example  (asked T8, 2026-07-22)
- prior-employer-exposure: yes — see 01-company/open-questions.md (asked T3, 2026-07-21)
- regulated-vertical: yes — handles other people's personal data (asked T3, 2026-07-21)
- password-manager: yes, 2FA on (attested T1, 2026-07-20)
- scheduled-prompt: declined (asked T2, 2026-07-21)
```

**Rules**

- One line per answer: `key: value  (asked <task>, <date>)`.
- An answer here is **settled**: never ask it again unprompted.
- Any answer is revisable. When the founder says something that contradicts a stored
  answer ("actually, I have a website now"), update the line, say which task that
  re-opens, and set that task back to `not-started` on the next reconcile.
- Never infer an answer from context. Only a stated answer gets written here.

## Reading state you did not write

A folder built by v1 will not match this shape.
Treat any pre-existing file as evidence to be verified, never as a claim to be believed —
and never as something to be tidied without asking. See `reconcile.md`.
