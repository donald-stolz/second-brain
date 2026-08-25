---
name: archive-stale
description: Find stale or completed notes and move them to 04 Archive. Use when asked to archive old notes, clean up stale items, or archive completed projects.
---

# Archive Stale

## Stale Criteria

A note is considered stale if ANY of the following are true:
- `status` is `done`
- `status` is `stale`
- `status` is `inbox` AND `modified` date is older than 90 days

## Steps

1. Scan these folders for stale notes: 00 Inbox, 01 Projects, 02 Areas.
   - Read each folder's CONTEXT.md to get the note list.
   - For each note, read its frontmatter and check against the stale criteria above.
2. For each stale note found:
   a. Move the file to 04 Archive with `obsidian move path=<source> to=<destination>` (falls back to the Edit/Write tools if Obsidian isn't running — see AGENTS.md's Obsidian CLI section).
   b. Update the note's frontmatter with `obsidian property:set`:
      - Set `status` to `archived`
      - Update `modified` to today's date
   c. Remove the note's row from the source folder's CONTEXT.md.
   d. Add the note's row to 04 Archive/CONTEXT.md with the updated status.
3. Update the root CONTEXT.md note counts for all affected folders.
4. Report:
   - Number of notes archived from each source folder
   - Filenames and original status of each archived note
   - Any notes that matched criteria but were skipped (see below)

## When Not to Use

- NEVER archive notes with `status: active` regardless of how old they are — active notes are by definition not stale.
- Do not archive notes already in 04 Archive — they are already archived.
- Do not archive MOC notes (type: moc) — they are structural and should remain in 03 Resources.
- Do not archive Daily Notes (type: daily) — use a separate cleanup process for those.
