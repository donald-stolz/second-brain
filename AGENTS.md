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

## Skills

Composable skills are available in `.agents/skills/`. Read a skill's SKILL.md for step-by-step instructions on common vault operations.
