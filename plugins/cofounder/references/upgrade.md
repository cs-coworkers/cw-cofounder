---
repo: product-cofounder
---

# Getting the next week

The plugin ships **one week per release**. A founder installs once and updates; a new week
is a version of the same plugin, never a second plugin and never a file to merge by hand.

Their venture folder is untouched by any of this. Updating the plugin cannot alter
`progress.md`, their artifacts, or their answers — the plugin is protocol only, and every
week they have already verified is carried forward verbatim.

## When to say this

Reconcile step 3 finds every installed week complete. There is no current task. Say so
plainly, then give them the steps below. Do **not** imply the program is over, and do not
invent a task to fill the gap.

> That's Week 1 finished — all nine tasks verified. Nothing here expires; everything you
> built stays exactly where it is.
>
> Week 2 arrives as an update to me rather than a new document. Here's how to pick it up
> when you're ready — it takes about a minute.

Then the steps. If they say they'd rather not right now, leave it: nothing breaks, and
`status` will still show them where they are.

## The word collision

`update` is already a founder verb meaning *re-read my files*, and the Cowork button for
getting a new release is also called update. The founder will not distinguish them. When they
say it near anything about a new week, versions, or installing, ask which they mean in one
line — `cofounder-update` carries the same rule. Never sweep their inputs when they were
asking for Week 2, and never send them to Customize when they just added a document.

## The steps (Cowork)

1. Open **Customize**.
2. Find the **cw-cofounder** marketplace entry and choose **update** — *not* install; it is
   already installed.
3. Reopen the marketplace entry and install the newer **cofounder** version.
4. Start a new session in the venture folder and say **continue**.

**The failure mode to warn them about, before they hit it.** Cowork caches a snapshot of
the marketplace. If the entry is not refreshed first, the new version simply does not appear
— no error, nothing to click, and the founder concludes it is broken. If update does not
surface the new version, **remove the marketplace entry and add it again**; the plugin
reinstalls clean and their folder is unaffected.

Say this *before* they go looking, not after they report it missing:

> One quirk worth knowing: the list you install from is cached, so the new version may not
> show up until you refresh it. If you don't see it, remove the cw-cofounder entry and add it
> back — that's a five-second fix and it can't touch your work.

## Confirming it landed

After they say **continue** in a new session, reconcile re-lists
`references/tasks/week-*/`. The new week appears in `weeks-installed`, gets its own section
in `progress.md`, and becomes `current-week`. Their completed weeks are read and carried
forward, never re-verified.

If they say they updated but `weeks-installed` has not changed, the marketplace snapshot is
stale — walk them through remove-and-re-add. Do not tell them to reinstall from scratch, and
never suggest touching the venture folder.

## Our side — what shipping a week means

Not founder-facing. A week release is:

1. `references/tasks/week-<N>/` added — the only structural change. Never edit a shipped
   week's task files to fit a new one; a founder mid-week-N is reading them live.
2. Stall codes for the new tasks registered in `reconcile.md` under `W<N>-T<n>-<reason>`.
   Product-level failures stay `CF-`.
3. `plugin.json` version bumped — **major = week number** (Week 1 = `1.x`, Week 2 = `2.x`);
   pre-release stays `0.x`. Unconventional semver, chosen because a founder reading
   "version 3" should be able to tell it is Week 3. Reversible if it ever costs us
   something; it is a label, not a dependency contract.
4. `CHANGELOG.md` entry naming the week and anything a mid-flight founder would notice.
5. The marketplace description's week count updated — it is the only place a prospective
   founder sees how far the program currently runs.
