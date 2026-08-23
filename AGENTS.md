# Second Brain — Agent Instructions

## Vault Overview

This is a PARA-organized Obsidian vault. Every note is a Markdown file with YAML frontmatter.

| Folder | Purpose | Note types |
|---|---|---|
| 00 Inbox | Unsorted capture. The front door for anything new. | inbox |
| 01 Projects | Short-term efforts with a defined outcome and deadline. | project |
| 02 Areas | Ongoing responsibilities with a standard to maintain. | area |
| 03 Resources | Topics of ongoing interest, kept for future reference. | resource, moc |
| 04 Archive | Inactive items from the other three categories. | any (archived) |
| Templates | Templater templates for creating new notes. | N/A |

Notes move between folders as their status changes. A completed project moves to 04 Archive. A resource that becomes actionable moves to 01 Projects.

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

## Safety Boundaries

Do NOT write to, modify, or delete files in these paths:
- `Templates/` — read-only reference for note structure
- `.obsidian/` — Obsidian plugin configuration

When editing any note:
- ALWAYS preserve existing wikilinks (`[[Note Name]]`)
- ALWAYS preserve existing YAML frontmatter fields (add fields, never remove)
- ALWAYS update the `modified` field to today's date when changing a note
- NEVER change the `created` field

## CONTEXT.md Index System

This vault uses a two-tier CONTEXT.md index:

1. Root `CONTEXT.md` — lists all folders with note counts and one-line summaries
2. Per-folder `CONTEXT.md` — lists every note in that folder with type, status, and summary

When you create, move, or delete a note:
1. Update the source folder's CONTEXT.md (remove the row if moving/deleting)
2. Update the destination folder's CONTEXT.md (add a row if moving/creating)
3. Update the root CONTEXT.md note counts

## Skills

Composable skills are available in `.agents/skills/`. Read a skill's SKILL.md for step-by-step instructions on common vault operations.
