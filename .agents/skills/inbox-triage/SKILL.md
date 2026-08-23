---
name: inbox-triage
description: Triage a note from 00 Inbox into the correct PARA folder. Use when asked to process inbox, sort inbox, triage notes, or clear the inbox.
---

# Inbox Triage

## Steps

1. Read the root CONTEXT.md to confirm there are notes in 00 Inbox.
2. Read 00 Inbox/CONTEXT.md to get the list of notes to triage.
3. For each inbox note:
   a. Read the note's content and frontmatter.
   b. Determine the correct PARA category based on content:
      - Has a clear outcome and deadline → 01 Projects (type: project)
      - Is an ongoing responsibility → 02 Areas (type: area)
      - Is reference material, article, or learning → 03 Resources (type: resource)
      - Cannot be categorized → leave in 00 Inbox and skip
   c. Move the file to the destination folder.
   d. Update the note's frontmatter:
      - Change `type` to match the destination folder
      - Change `status` from `inbox` to `active`
      - Update `modified` to today's date
   e. Remove the note's row from 00 Inbox/CONTEXT.md.
   f. Add the note's row to the destination folder's CONTEXT.md.
4. Update the root CONTEXT.md note counts.
5. Report what was triaged and where each note landed.

## When Not to Use

- Do not triage notes that have `status: active` — they were already processed.
- Do not move Daily Notes (type: daily) out of the Inbox.
