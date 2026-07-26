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
`cf-status` will still show them where they are.

## The word collision

`cf-update` is unambiguous — it means *re-read my files* and nothing else. The **bare** word
is not: "update" is a live alias for that verb *and* the name of the Cowork button that fetches
a new release. The founder will not distinguish them. When they say the bare word near anything
about a new week, versions, or installing, ask which they mean in one line. Never sweep their
inputs when they were asking for Week 2, and never send them to Customize when they just added
a document.

## The steps (Cowork)

1. Open **Customize**.
2. Find the **cw-cofounder** marketplace entry and choose **update** — *not* install; it is
   already installed.
3. Reopen the marketplace entry and install the newer **cofounder** version.
4. Start a new session in the venture folder and say **cf-continue**.

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

After they say **cf-continue** in a new session, reconcile re-lists
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
   **Any new founder verb carries the `cf-` prefix, and its skill is named for it exactly**
   — see `voice.md` § The founder's three verbs. Bare words may be added as silent aliases;
   they may never be the taught verb.
3. `plugin.json` version bumped — **major = week number** (Week 1 = `1.x`, Week 2 = `2.x`);
   pre-release stays `0.x`. Unconventional semver, chosen because a founder reading
   "version 3" should be able to tell it is Week 3. Reversible if it ever costs us
   something; it is a label, not a dependency contract.
4. `CHANGELOG.md` entry naming the week and anything a mid-flight founder would notice.
5. The marketplace description's week count updated — it is the only place a prospective
   founder sees how far the program currently runs.
6. **The shippable set synced to `cs-coworkers/cw-cofounder`** — the public product repo, and
   the only place a founder can install from. `cw-plugins` is the dev home (internal README,
   `evals/`, history); `cw-cofounder` is release-only and carries the product alone. Nothing
   reaches a founder until this step runs.

**The sync, concretely.** Copy `plugins/cofounder/` from `cw-plugins` to `cw-cofounder`,
**excluding** `README.md` (internal notes) and `evals/` (our test material); the public repo
keeps its own root `README.md` and `.claude-plugin/marketplace.json`. Every other file must
be byte-identical in both repos at release.

**A plain copy is not enough when anything was renamed or deleted** — it adds the new path and
leaves the old one sitting there, so the public repo ships both. A stale skill directory still
registers its skill, which means the founder gets two skills answering one verb. Mirror the
rename in the public repo first (`git mv`, which keeps its history), *then* copy. Learned doing
exactly this on 2026-07-24, when `cofounder-*` → `cf-*` would have left three orphaned skills
live in the product.

Verify before tagging — the `diff -r` catches an orphan as an `Only in …` line, which is why
the pass condition is empty output and not "no differences reported":

```bash
diff -r --strip-trailing-cr -x README.md -x evals \
  cw-plugins/plugins/cofounder cw-cofounder/plugins/cofounder
```

Empty output is the pass condition.

**`--strip-trailing-cr` is load-bearing on Windows, not tidiness.** With `core.autocrlf` on,
any checkout re-materializes that repo's working tree with CRLF while the other stays LF, and
the diff then reports *every file* as differing — a total false failure, arriving precisely when
someone is about to ship. The trap is the obvious repair: re-copy and commit, which pushes CRLF
into the public repo for real. Seen 2026-07-26, immediately after a `git checkout main`.

When the answer matters — before tagging, or when a diff looks implausible — settle it against
git rather than the working tree, which cannot lie about line endings:

```bash
git -C cw-plugins   ls-tree -r HEAD --format='%(objectname) %(path)' plugins/cofounder \
  | grep -vE 'README.md|/evals/' | sed 's|plugins/cofounder/||' | sort > /tmp/dev.txt
git -C cw-cofounder ls-tree -r HEAD --format='%(objectname) %(path)' plugins/cofounder \
  | grep -vE 'README.md|/evals/' | sed 's|plugins/cofounder/||' | sort > /tmp/pub.txt
diff /tmp/dev.txt /tmp/pub.txt
```

Identical blob hashes for identical paths is proof of byte-identical *committed* content, which
is what actually ships. Empty output passes; 18 shipped files at `v0.3.0`. A fix that lands in one repo and not the other ships a
plugin nobody reviewed — and because the public copy is the one founders install, the repo we
read during review would not be the repo they run. Sync on every change to a shipped file, not
only on week releases.

**Then check the two files the diff cannot see.** `cw-cofounder`'s root `README.md` and
`marketplace.json` are excluded from the parity check because they legitimately differ from
the dev repo — which means nothing will ever tell you they went stale. The public README is
the founder's first contact with the product and it carries the verb table, the install steps,
and the version number; all three drift silently. After any sync, grep it for the verbs and
the version:

```bash
grep -nE 'cf-(continue|update|status)|v0\.[0-9]+\.[0-9]+' cw-cofounder/README.md
```

Missed on 2026-07-24: the verb rename landed everywhere the diff could reach, and left the
public README teaching the old bare words to every founder who opened the repo page.

## Gate status — one source, two copies

**Gate state is derived, never authored.** The single source is the gate run records in
`…/campaigns/active/building-with-managed-agents/assets/`, one per gate, and specifically their
frontmatter: `gate:` names which gate, `status:` is its verdict. A gate with no record has not
run. Nothing else may assert a gate's state on its own authority — if a string somewhere says a
gate passed, it is quoting a record or it is wrong.

There are exactly two copies, and **both sit outside the parity diff**: the dev
`cw-plugins/.claude-plugin/marketplace.json` entry (not under `plugins/cofounder/` at all) and
the public `cw-cofounder/.claude-plugin/marketplace.json` entry (excluded by design). So neither
is ever reported stale by anything above. Regenerate both from the records at every release, and
at any point a gate's verdict changes — a gate verdict lands on a different day from a version
bump, which is exactly how it goes unnoticed.

The two audiences differ and should stay different: the dev entry names gates by number, because
we read it; the public entry says only that the product is early access with gates outstanding,
because a founder does not have our gate vocabulary and numbering it invites them to ask which
gate they are. Both must still be *true*.

```bash
grep -noE 'UNRELEASED|[Ee]arly access|[Gg]ates? [0-9]+|gates? pending|PASSED [0-9-]+' \
  cw-plugins/.claude-plugin/marketplace.json cw-cofounder/.claude-plugin/marketplace.json
```

The pass condition is that every gate claim printed matches a run record's `status:`, and no
string claims or implies a gate that has no record. Unlike the parity diff, empty output is a
**failure** here — it means the status vocabulary was reworded and this grep has gone blind.

Added 2026-07-26, after the third silent status drift in three days: the rename-unsafe sync, the
excluded public README, and the dev marketplace entry still reading "Gate 2 pending" two days
after Gate 2 passed. All three are one shape — **a string nothing checks, describing state that
lives somewhere else.** The general guard is the one that retires the class: name the source,
keep the copies countable, and grep them.
