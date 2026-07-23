# Claude Co-Founder

*Building With Managed Agents* as something you run, not something you read.

The series teaches the method in public. This repo holds the plugin that executes it: your
agent walks you through each week's tasks one at a time, checks that each one actually
worked before offering the next, and can be re-run any number of times without losing your
place.

**Week 1 is the first release.** Later weeks arrive as updates to this same plugin — install
once, update as they ship.

## Three words

You only ever need three:

| Say | What happens |
|---|---|
| **continue** | Works out where you actually are from the files in your folder, tells you, and runs the task that comes next. Start every session with this. |
| **update** | You added or changed files in your inputs folder — re-read them and fold in what's new, without overwriting what's already there. Any time, any number of times. |
| **status** | The map: what's done, what's next, what's stuck. Changes nothing. |

## Your work stays yours

The plugin is protocol only. Everything you produce — your progress, your answers, your
company files, your artifacts — lives in your own venture folder on your own machine.
Installing, updating or removing the plugin never touches any of it.

## Installing

You install this through **Customize** in the Cowork app: add the marketplace, then install
the plugin. Two steps, in that order.

```
Marketplace: https://github.com/cs-coworkers/cw-cofounder
Plugin:      cofounder
```

Then open a session in your venture folder and say **continue**.

If you are picking up a later week and the new version doesn't appear, the plugin list is
cached — remove the marketplace entry and add it back. That can't affect your folder.

## Status

**Early access, and honestly labelled: not finished.** This is `v0.2.0`, unreleased, with
its acceptance gates still open. If something stalls, the agent will give you a short code
— send it to us, it tells us exactly where it broke.

---

Made by [Coworkers.Global](https://coworkers.global). All rights reserved.
