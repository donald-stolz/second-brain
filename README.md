# Second Brain

A personal knowledge management vault built for [Obsidian](https://obsidian.md), organized with the **PARA method** from Tiago Forte's *Building a Second Brain*.

## What this repo is

This repo shares the *structure* of the vault, not its contents. Every actual note — projects, areas, resources, archives, daily notes, clippings — stays local and untracked. Only this README and the per-folder `README.md` files are version-controlled, so the organizational system can be reused or referenced without exposing personal information.

See `.gitignore` for how that's enforced: everything is ignored by default except `README.md` files.

## Structure

| Folder | Purpose |
|---|---|
| [`00 Inbox`](./00%20Inbox/README.md) | Unsorted capture — the front door for anything new |
| [`01 Projects`](./01%20Projects/README.md) | Short-term efforts with a defined outcome and deadline |
| [`02 Areas`](./02%20Areas/README.md) | Ongoing responsibilities with a standard to maintain |
| [`03 Resources`](./03%20Resources/README.md) | Topics of ongoing interest, kept for future reference |
| [`04 Archive`](./04%20Archive/README.md) | Inactive items from the other three categories |
| [`Templates`](./Templates/README.md) | Templater templates used to create new notes |

## The PARA method, briefly

PARA sorts everything by **actionability**, not by topic:

1. **Projects** — active, have an end date
2. **Areas** — ongoing, no end date, but a standard to uphold
3. **Resources** — reference material, no obligation attached
4. **Archive** — anything no longer active from the above three

Items move between categories as their status changes (e.g., a completed Project moves to Archive; a Resource that becomes actionable moves to Projects).
