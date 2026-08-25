# Second Brain — Agent Instructions

## Vault Overview

This is a PARA-organized Obsidian vault. Every note is a Markdown file with YAML frontmatter.

| Folder | Purpose | Note types |
|---|---|---|
| 00 Inbox | Unsorted capture. The front door for anything new. | inbox, daily (in `00 Inbox/Daily Plan/` — see below) |
| 01 Projects | Short-term efforts with a defined outcome and deadline. | project |
| 02 Areas | Ongoing responsibilities with a standard to maintain. | area |
| 03 Resources | Topics of ongoing interest, kept for future reference. | resource, moc |
| 04 Archive | Inactive items from the other three categories. | any (archived) |
| Templates | Templater templates for creating new notes. | N/A |

Notes move between folders as their status changes. A completed project moves to 04 Archive. A resource that becomes actionable moves to 01 Projects.

`00 Inbox/Daily Plan/` is an exception to that lifecycle: it holds daily Todo notes (Top 3 + regular checklist, `type: daily`, created from `Templates/Todo Note.md`) managed by the `daily-review` skill. They live there permanently — never triaged, never archived. See `.agents/skills/daily-review/SKILL.md`.

## Frontmatter Schema

Every note carries these universal fields in YAML frontmatter:

| Field | Required | Values |
|---|---|---|
| type | Yes | inbox, project, area, resource, moc, daily |
| status | Yes | inbox, active, done, stale, archived |
| created | Yes | YYYY-MM-DD |
| modified | Yes | YYYY-MM-DD |
| summary | Yes | One-line description of the note |
| tags | Yes | List of lowercase tags |

Resource notes add two extra fields:

| Field | Required | Values |
|---|---|---|
| source | Resource only | URL, book title, or reference |
| source_type | Resource only | article, book, podcast, video, course, conversation, email |

## File Naming Conventions

- Note filenames use title case with spaces: `Meeting Notes From Standup.md`
- No special characters in filenames except hyphens and spaces
- Templates are named by type: `Inbox Note.md`, `Project Note.md`, etc.
- Exception: Daily Plan Todo notes are named by date, `Todo-YYYY-MM-DD.md`

## Safety Boundaries

Do NOT write to, modify, or delete files in these paths:
- `.obsidian/` — Obsidian plugin configuration

`Templates/` is normally read-only reference for note structure. Only edit a file in `Templates/` when the user makes a specific request to change that template, and confirm the change with them before writing.

When editing any note:
- ALWAYS preserve existing wikilinks (`[[Note Name]]`)
- ALWAYS preserve existing YAML frontmatter fields (add fields, never remove)
- ALWAYS update the `modified` field to today's date when changing a note
- NEVER change the `created` field

## CONTEXT.md Index System

This vault uses a two-tier CONTEXT.md index:

1. Root `CONTEXT.md` — lists all folders with note counts and one-line summaries
2. Per-folder `CONTEXT.md` — lists every note in that folder with type, status, and summary

Exception: `00 Inbox/Daily Plan/` has its own nested `CONTEXT.md`, referenced by a "Subfolders" table in `00 Inbox/CONTEXT.md` — the same pattern the root index uses for PARA folders.

When you create, move, or delete a note:
1. Update the source folder's CONTEXT.md (remove the row if moving/deleting)
2. Update the destination folder's CONTEXT.md (add a row if moving/creating)
3. Update the root CONTEXT.md note counts

## Obsidian CLI

The `obsidian` CLI drives the actual running Obsidian app — it is not a filesystem tool. Commands only work while Obsidian is open on this machine, and they act on the active vault.

**Prefer it over raw Read/Edit/Write for the operations it covers.** Edits made through Obsidian's own APIs (`move`, `rename`, `delete`, `property:set`, `create`, `append`, `prepend`) are recognized by Obsidian Sync immediately, same as a manual edit in the app. Edits made by writing directly to disk (the Read/Edit/Write tools) sit outside the app until Obsidian notices the external change on its own — which only happens once Obsidian is reopened, and can lag or get missed depending on sync state. If you end up editing notes via raw file tools while Obsidian is closed, tell the user those changes won't reach their other devices until they reopen Obsidian here.

If an `obsidian` command errors because the app isn't running, fall back to the raw file tools and flag the sync caveat above.

Common operations relevant to this vault's skills:

| Task | Command |
|---|---|
| Move a note between PARA folders (link-safe) | `obsidian move path=<path> to=<path>` |
| Rename a note | `obsidian rename path=<path> name=<name>` |
| Delete a note | `obsidian delete path=<path>` |
| Read / set / remove a frontmatter field | `obsidian property:read` / `property:set` / `property:remove` `name=<field> path=<path>` |
| Create a note from a Templater template (resolves `<% %>` syntax and dates) | `obsidian templater:create-from-template template=<path> file=<path>` |
| Full-text search the vault | `obsidian search query=<text>` (or `search:context` for line context) |
| Notes with no incoming / no outgoing links | `obsidian orphans` / `obsidian deadends` |
| Broken wikilinks | `obsidian unresolved` |
| Backlinks to a note (check before adding a link) | `obsidian backlinks path=<path>` |
| Tags / frontmatter properties, vault-wide, with counts | `obsidian tags counts` / `obsidian properties counts` |
| List or toggle tasks (e.g. in a daily note) | `obsidian tasks` / `obsidian task toggle` |

Run `obsidian help <command>` for full option lists. Operations without a CLI equivalent — writing CONTEXT.md tables, inserting a wikilink into a specific section of a note — still go through the normal Read/Edit/Write tools.

## Skills

Composable skills are available in `.agents/skills/`. Read a skill's SKILL.md for step-by-step instructions on common vault operations. Skills that move, create, or edit frontmatter on notes use the `obsidian` CLI commands above where applicable.
