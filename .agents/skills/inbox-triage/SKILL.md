---
name: inbox-triage
description: Triage a note from 00 Inbox into the correct PARA folder. Use when asked to process inbox, sort inbox, triage notes, or clear the inbox.
---

# Inbox Triage

## Steps

1. Read the root CONTEXT.md to confirm there are notes in 00 Inbox.
2. Read 00 Inbox/CONTEXT.md to get the list of notes to triage. This is the top-level note table only — it does not include `00 Inbox/Daily Plan/`, which has its own nested index and is never triaged, or `00 Inbox/daily-notes/`, which uses the separate scratchpad process below.
3. For each inbox note:
   a. Read the note's content and frontmatter.
   b. Determine the correct PARA category based on content:
      - Has a clear outcome and deadline → 01 Projects (type: project)
      - Is an ongoing responsibility → 02 Areas (type: area)
      - Is reference material, article, or learning → 03 Resources (type: resource)
      - Cannot be categorized → leave in 00 Inbox and skip
   c. Move the file to the destination folder with `obsidian move path=<source> to=<destination>` (falls back to the Edit/Write tools if Obsidian isn't running — see AGENTS.md's Obsidian CLI section).
   d. Update the note's frontmatter with `obsidian property:set`:
      - Change `type` to match the destination folder
      - Change `status` from `inbox` to `active`
      - Update `modified` to today's date
   e. Remove the note's row from 00 Inbox/CONTEXT.md.
   f. Add the note's row to the destination folder's CONTEXT.md.
4. Also process `00 Inbox/daily-notes/` scratchpad files — see below.
5. Update the root CONTEXT.md note counts.
6. Report what was triaged and where each note (and each scratchpad item) landed.

## Daily Notes Scratchpad (`00 Inbox/daily-notes/`)

`00 Inbox/daily-notes/` holds raw, frontmatter-less capture files named `YYYY-MM-DD.md`. Each one typically mixes several unrelated topics in a single file (meeting notes, video/article notes, stray tasks, ideas). They are not proper vault notes and are not listed in any CONTEXT.md, so they are never moved or re-typed as a whole file the way top-level inbox notes are. Instead, process each file's *content* item by item:

1. List files in `00 Inbox/daily-notes/`.
2. Read one file and split its content into logical items — a heading/bullet cluster that covers one topic each.
3. For each item, decide:
   - **Belongs to an existing note** → merge/append the content into that note's relevant section (use `obsidian search` or `backlinks` to find candidates), and update the target note's `modified` field to today.
   - **Warrants a new note** → create it from the matching template (`Templates/Project Note.md`, `Area Note.md`, or `Resource Note.md`) with full frontmatter, using the same category rules as step 3b above. Register it in the destination folder's CONTEXT.md and update root counts.
   - **Not actionable / too vague to place** → leave it out of any note; call it out in the final report so the user can decide.
4. Once every item in the file has been merged, promoted, or explicitly called out as not-actionable, move the file to `04 Archive/daily-notes/` with `obsidian move` (create the subfolder if needed). Do not archive a file with items still unresolved — leave it in place and report what's pending.
5. Repeat for each file in the folder.

## When Not to Use

- Do not triage notes that have `status: active` — they were already processed.
- Do not touch `00 Inbox/Daily Plan/` — those `type: daily` Todo notes live there permanently and are managed by the `daily-review` skill, not triage.
